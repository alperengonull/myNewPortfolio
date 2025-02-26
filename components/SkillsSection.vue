<template>
  <section id="skills" class="min-h-screen py-20 relative">
    <div class="container mx-auto px-6">
      <h2 class="text-4xl font-bold mb-16 text-center">Skills</h2>
      <div class="relative h-[600px]">
        <div id="brain-container" class="absolute inset-0 z-10"></div>
        <div class="absolute inset-0">
          <div class="relative h-full">
            <template v-for="(tech, index) in technologies" :key="tech.id">
              <div
                :class="[
                  'technology-item absolute transform -translate-x-1/2 -translate-y-1/2',
                  'transition-all duration-300 hover:scale-110',
                ]"
                :style="{
                  left: `${
                    50 +
                    35 * Math.cos((index * (2 * Math.PI)) / technologies.length)
                  }%`,
                  top: `${
                    50 +
                    35 * Math.sin((index * (2 * Math.PI)) / technologies.length)
                  }%`,
                }"
                @mouseenter="highlightTechnology(index)"
                @mouseleave="resetHighlight"
              >
                <div
                  class="bg-gray-800/50 backdrop-blur-sm p-4 rounded-xl hover:bg-gray-700/50 transition-colors"
                >
                  <img
                    :src="tech.icon"
                    :alt="tech.name"
                    class="w-12 h-12 mb-2"
                  />
                  <p class="text-sm font-medium text-center">{{ tech.name }}</p>
                </div>
              </div>
            </template>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
  
<script setup lang="ts">
import * as THREE from "three";
import { GLTFLoader } from "three/examples/jsm/loaders/GLTFLoader.js";
import { gsap } from "gsap";
import vueIcon from "@/assets/icons/vue.svg";
import reactIcon from "@/assets/icons/react.svg";
import nuxtIcon from "@/assets/icons/nuxt.svg";
import jsIcon from "@/assets/icons/javascript.svg";
import tsIcon from "@/assets/icons/typescript.svg";
import tailwindIcon from "@/assets/icons/tailwind.svg";

const technologies = [
  { id: 1, name: "Vue.js", icon: vueIcon },
  { id: 2, name: "React Native", icon: reactIcon },
  { id: 3, name: "Nuxt.js", icon: nuxtIcon },
  { id: 4, name: "JavaScript", icon: jsIcon },
  { id: 5, name: "TypeScript", icon: tsIcon },
  { id: 6, name: "Tailwind CSS", icon: tailwindIcon },
];

let scene: THREE.Scene;
let camera: THREE.PerspectiveCamera;
let renderer: THREE.WebGLRenderer;
let brainModel: THREE.Group;

onMounted(() => {
  initThreeJS();
  loadBrainModel();
});

function initThreeJS() {
  const container = document.getElementById("brain-container");
  if (!container) return;

  scene = new THREE.Scene();
  camera = new THREE.PerspectiveCamera(
    75,
    container.clientWidth / container.clientHeight,
    0.1,
    1000
  );
  renderer = new THREE.WebGLRenderer({
    alpha: true,
    antialias: true,
    powerPreference: "high-performance",
  });

  renderer.setSize(container.clientWidth, container.clientHeight);
  renderer.setPixelRatio(window.devicePixelRatio);
  container.appendChild(renderer.domElement);

  const ambientLight = new THREE.AmbientLight(0xffffff, 0.5);
  scene.add(ambientLight);

  const frontLight = new THREE.DirectionalLight(0xffffff, 1);
  frontLight.position.set(0, 0, 10);

  const topLight = new THREE.DirectionalLight(0xffffff, 1);
  topLight.position.set(0, 10, 0);

  const leftLight = new THREE.DirectionalLight(0x6366f1, 0.5);
  leftLight.position.set(-10, 0, 0);

  const rightLight = new THREE.DirectionalLight(0x6366f1, 0.5);
  rightLight.position.set(10, 0, 0);

  scene.add(frontLight, topLight, leftLight, rightLight);

  camera.position.z = 12;
  camera.position.y = 3;

  window.addEventListener("resize", () => {
    camera.aspect = container.clientWidth / container.clientHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(container.clientWidth, container.clientHeight);
  });

  animate();
}

function loadBrainModel() {
  const loader = new GLTFLoader();
  loader.load(
    "/models/stylizedhumanbrain.glb",
    (gltf: any) => {
      scene.remove(brainModel);

      brainModel = gltf.scene;

      brainModel.position.set(0, 0, 0);
      brainModel.scale.set(100, 100, 100);

      brainModel.rotation.x = -0.2;

      brainModel.traverse((child) => {
        if (child instanceof THREE.Mesh) {
          child.material = new THREE.MeshPhysicalMaterial({
            color: 0x6366f1,
            emissive: 0x2a2a5a,
            metalness: 0.3,
            roughness: 0.4,
            transparent: true,
            opacity: 0.9,
            clearcoat: 0.3,
            clearcoatRoughness: 0.25,
          });
        }
      });

      scene.add(brainModel);

      camera.position.z = 12;
      camera.position.y = 3;
    },
    (xhr: any) => {
      console.log((xhr.loaded / xhr.total) * 100 + "% yüklendi");
    },
    (error: any) => {
      console.error("Model yüklenirken hata:", error);
    }
  );
}

function highlightTechnology(index: number) {
  if (brainModel) {
    const targetRotation = (index * Math.PI * 2) / technologies.length;
    gsap.to(brainModel.rotation, {
      y: targetRotation,
      duration: 0.5, // Hızlandırıldı
      ease: "power2.out",
    });

    const tiltAngle = 0.2;
    gsap.to(brainModel.rotation, {
      x: -Math.cos(targetRotation) * tiltAngle,
      z: Math.sin(targetRotation) * tiltAngle,
      duration: 0.5, // Hızlandırıldı
      ease: "power2.out",
    });
  }
}

function resetHighlight() {
  if (brainModel) {
    gsap.to(brainModel.rotation, {
      x: -0.2,
      y: brainModel.rotation.y,
      z: 0,
      duration: 1,
      ease: "power2.out",
    });
  }
}

function animate() {
  requestAnimationFrame(animate);
  if (brainModel) {
    brainModel.rotation.y += 0.002;

    const time = Date.now() * 0.001;
    brainModel.position.y = Math.sin(time) * 0.1;
    brainModel.rotation.z = Math.sin(time * 0.5) * 0.05;
  }
  renderer.render(scene, camera);
}
</script>
  
<style scoped>
#brain-container {
  background: transparent;
  pointer-events: none;
}

.technology-item {
  pointer-events: auto;
}

.technology-item {
  opacity: 0;
  animation: fadeIn 0.5s ease-out forwards;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translate(-50%, -50%) scale(0.8);
  }
  to {
    opacity: 1;
    transform: translate(-50%, -50%) scale(1);
  }
}

.technology-item:nth-child(1) {
  animation-delay: 0.1s;
}
.technology-item:nth-child(2) {
  animation-delay: 0.2s;
}
.technology-item:nth-child(3) {
  animation-delay: 0.3s;
}
.technology-item:nth-child(4) {
  animation-delay: 0.4s;
}
.technology-item:nth-child(5) {
  animation-delay: 0.5s;
}
.technology-item:nth-child(6) {
  animation-delay: 0.6s;
}

@media (max-width: 768px) {
  #brain-container {
    margin-top: 240px;
    margin-left: 50px;
    height: 200px;
    width: 300px;
  }

  .technology-item {
    width: 100px;
    height: 100px;
  }

  .technology-item img {
    width: 24px;
    height: 24px;
    margin-left: 20px;
  }

  .technology-item p {
    font-size: 0.75rem;
  }
}
</style>