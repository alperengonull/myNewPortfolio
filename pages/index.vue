<template>
  <main>
    <!-- Hero Section -->
    <section id="home" class="h-screen flex items-center justify-center relative">
      <div class="container mx-auto px-6 z-10 flex flex-col md:flex-row items-center">
        <div class="text-center md:text-left md:w-1/2">
          <h1 class="text-5xl md:text-7xl font-bold mb-6 typing-text">
            <!-- Text will be typed here -->
          </h1>
          <p class="text-xl md:text-2xl text-gray-300 mb-8">
            A passionate frontend developer and mobile developer from Turkey.
          </p>
          <a
            href="/about"
            class="bg-blue-500 hover:bg-blue-600 text-white px-8 py-3 rounded-full transition-colors"
          >
            More About me
          </a>
        </div>
        <div class="mt-8 md:mt-0 md:w-1/2 flex justify-center">
          <img
            src="../assets/images/linkedin_profile.jpg"
            alt="Your Picture"
            class="w-48 h-48 md:w-64 md:h-64 rounded-full object-cover"
          />
        </div>
      </div>
    </section>
    <!-- Skills Section -->
    <SkillsSection />
    <!-- wave line -->
    <div class="wave-border top">
      <svg
        viewBox="0 0 500 150"
        preserveAspectRatio="none"
        style="height: 100%; width: 100%"
        role="presentation"
      >
        <path
          d="M0.00,49.98 C149.99,150.00 349.20,-49.98 500.00,49.98 L500.00,150.00 L0.00,150.00 Z"
          style="stroke: none; fill: var(--shade-100)"
        ></path>
        <path
          class="neon-path"
          d="M0.00,49.98 C149.99,150.00 349.20,-49.98 500.00,49.98"
          style="stroke: var(--neon-color); fill: none"
        ></path>
      </svg>
    </div>
    <!-- Projects Section -->
    <section id="projects" class="py-20">
      <div class="container mx-auto px-6">
        <h2 class="text-4xl font-bold mb-12 text-center">Featured Projects</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            class="relative bg-gray-800 p-6 rounded-lg shadow-lg hover:bg-gray-700 transition-colors"
          >
            <div class="relative group">
              <img
                src="../assets/images/project.png"
                alt="Project 1"
                class="w-full h-48 object-cover rounded-t-lg mb-4 group-hover:opacity-75 transition-opacity"
              />
              <a
                href="http://otokurtarmaadana.com"
                class="absolute inset-0 flex items-center justify-center bg-black bg-opacity-50 opacity-0 group-hover:opacity-100 transition-opacity"
              >
                <span class="bg-blue-500 text-white px-4 py-2 rounded-full">Live</span>
              </a>
            </div>
            <h3 class="text-2xl font-bold mb-2">Auto rescue</h3>
            <p class="text-gray-400 mb-4">A browser for auto rescue.</p>
            <div class="flex flex-wrap space-x-2 mb-4">
              <span class="bg-blue-500 text-white px-3 py-1 rounded-full text-sm">Nuxt</span>
              <span class="bg-blue-500 text-white px-3 py-1 rounded-full text-sm">Tailwind</span>
              <span class="bg-blue-500 text-white px-3 py-1 rounded-full text-sm">JS</span>
            </div>
          </div>
          <div
            class="relative bg-gray-800 p-6 rounded-lg shadow-lg hover:bg-gray-700 transition-colors"
          >
            <div class="relative group">
              <img
                src="../assets/images/project2.png"
                alt="Project 2"
                class="w-full h-48 object-cover rounded-t-lg mb-4 group-hover:opacity-75 transition-opacity cursor-pointer"
                onclick="document.getElementById('videoModal').showModal();"
              />
             
            </div>
            <!-- ✅ Responsive Modal -->
            <dialog id="videoModal" class="backdrop:bg-black backdrop:bg-opacity-75 p-4 rounded-lg w-full max-w-3xl">
              <div class="flex flex-col items-center">
                <video class="w-full max-h-[80vh] rounded-lg" controls>
                  <source src="../assets/videos/CryptoPriceTrackerVideo.webm" type="video/webm">
                  Your browser does not support the video tag.
                </video>
                <button onclick="document.getElementById('videoModal').close();" 
                        class="mt-2 bg-red-500 text-white px-4 py-2 rounded-full">
                   ✖
                </button>
              </div>
            </dialog>
            <h3 class="text-2xl font-bold mb-2">Crypto Tracker Mobile App</h3>
            <p class="text-gray-400 mb-4">A browser for auto rescue.</p>
            <div class="flex flex-wrap space-x-2 mb-4">
              <span class="bg-blue-500 text-white px-3 py-1 mt-3 rounded-full text-sm">React Native</span>
              <span class="bg-blue-500 text-white px-3 py-1 mt-3 rounded-full text-sm">CSS</span>
              <span class="bg-blue-500 text-white px-3 py-1 mt-3 rounded-full text-sm">AsyncStorage</span>
              <span class="bg-blue-500 text-white px-3 py-1 mt-3 rounded-full text-sm">Firebase</span>
              <span class="bg-blue-500 text-white px-3 py-1 mt-3 rounded-full text-sm">Jotai</span>
            </div>
          </div>
          <!-- New project add -->
           <div
            class="relative bg-gray-800 p-6 rounded-lg shadow-lg hover:bg-gray-700 transition-colors"
          >
            <div class="relative group">
              <img
                src="../assets/images/lebenindeutschland.png"
                alt="Project 1"
                class="w-full h-48 object-cover rounded-t-lg mb-4 group-hover:opacity-75 transition-opacity"
              />
              <a
                href="https://play.google.com/store/apps/details?id=com.germanlangapp"
                class="absolute inset-0 flex items-center justify-center bg-black bg-opacity-50 opacity-0 group-hover:opacity-100 transition-opacity"
              >
                <span class="bg-blue-500 text-white px-4 py-2 rounded-full">Live</span>
              </a>
            </div>
            <h3 class="text-2xl font-bold mb-2">Leben In Deutschland</h3>
            <p class="text-gray-400 mb-4">Germany citizenship exam preparation application.</p>
            <div class="flex flex-wrap space-x-2 mb-4">
              <span class="bg-blue-500 text-white px-3 py-1 rounded-full text-sm mt-3">React Native</span>
              <span class="bg-blue-500 text-white px-3 py-1 rounded-full text-sm mt-3">AsyncStorage</span>
              <span class="bg-blue-500 text-white px-3 py-1 rounded-full text-sm mt-3">Gifted Charts</span>
               <span class="bg-blue-500 text-white px-3 py-1 rounded-full text-sm mt-3">Splash Screen</span>
               <span class="bg-blue-500 text-white px-3 py-1 rounded-full text-sm mt-3">React Native i18</span>
               <span class="bg-blue-500 text-white px-3 py-1 rounded-full text-sm mt-3">Navigation</span>
               <span class="bg-blue-500 text-white px-3 py-1 rounded-full text-sm mt-3">React Native Elements</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- wave line -->
    <div class="wave-border contact-wave top">
      <svg
        viewBox="0 0 500 150"
        preserveAspectRatio="none"
        style="height: 100%; width: 100%"
        role="presentation"
      >
        <path
          d="M0.00,49.98 C149.99,150.00 349.20,-49.98 500.00,49.98 L500.00,150.00 L0.00,150.00 Z"
          style="stroke: none; fill: var(--shade-100)"
        ></path>
        <path
          class="neon-path"
          d="M0.00,49.98 C149.99,150.00 349.20,-49.98 500.00,49.98"
          style="stroke: var(--neon-color); fill: none"
        ></path>
      </svg>
    </div>
    <!-- Contact Section -->
    <section id="contact" class="py-20">
      <div class="container mx-auto px-6">
        <h2 class="text-4xl font-bold mb-12 text-center">Contact with Me 👋</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
          <div class="relative bg-gray-800 p-6 rounded-lg shadow-lg">
            <h3 class="text-2xl font-bold mb-2">Get in touch</h3>
            <p class="text-gray-400 mb-4">
              I'm currently available for full time and freelance work. If you
              have a project that you want to get started, think you need my
              help with something or just fancy saying hey, then get in touch.
            </p>
            <div class="flex space-x-4 mt-4">
              <a
                href="https://linkedin.com/in/alperengonul"
                target="_blank"
                class="text-gray-400 hover:text-white transition-colors"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-6 w-6"
                  fill="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    d="M22.23 0H1.77C.79 0 0 .774 0 1.73v20.54C0 23.226.79 24 1.77 24h20.46c.98 0 1.77-.774 1.77-1.73V1.73C24 .774 23.21 0 22.23 0zM7.12 20.452H3.56V9h3.56v11.452zM5.34 7.548c-1.14 0-2.06-.92-2.06-2.06 0-1.14.92-2.06 2.06-2.06 1.14 0 2.06.92 2.06 2.06 0 1.14-.92 2.06-2.06 2.06zM20.452 20.452h-3.56v-5.6c0-1.34-.03-3.06-1.86-3.06-1.86 0-2.14 1.45-2.14 2.95v5.71h-3.56V9h3.42v1.56h.05c.48-.9 1.64-1.85 3.38-1.85 3.61 0 4.28 2.38 4.28 5.47v6.27z"
                  />
                </svg>
              </a>
              <a
                href="https://github.com/alperengonull"
                target="_blank"
                class="text-gray-400 hover:text-white transition-colors"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-6 w-6"
                  fill="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    d="M12 0C5.373 0 0 5.373 0 12c0 5.303 3.438 9.8 8.205 11.387.6.111.82-.261.82-.577 0-.285-.01-1.04-.015-2.04-3.338.726-4.042-1.61-4.042-1.61-.546-1.387-1.333-1.756-1.333-1.756-1.089-.744.083-.729.083-.729 1.205.084 1.838 1.237 1.838 1.237 1.07 1.834 2.809 1.304 3.495.997.108-.775.418-1.305.76-1.605-2.665-.305-5.466-1.332-5.466-5.931 0-1.31.467-2.381 1.235-3.221-.124-.303-.535-1.527.117-3.176 0 0 1.008-.322 3.3 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.29-1.552 3.296-1.23 3.296-1.23.653 1.649.242 2.873.118 3.176.77.84 1.233 1.911 1.233 3.221 0 4.61-2.804 5.624-5.475 5.921.43.371.814 1.102.814 2.222 0 1.606-.014 2.898-.014 3.293 0 .319.217.694.825.576C20.565 21.796 24 17.298 24 12c0-6.627-5.373-12-12-12z"
                  />
                </svg>
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup lang="ts">
import * as THREE from "three";

onMounted(() => {
  initThreeJS();
  typeEffect();
});

function initThreeJS() {
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(
    75,
    window.innerWidth / window.innerHeight,
    0.1,
    1000
  );
  const renderer = new THREE.WebGLRenderer({ alpha: true });
  renderer.setSize(window.innerWidth, window.innerHeight);
  const geometry = new THREE.TorusKnotGeometry(10, 3, 100, 16);
  const material = new THREE.MeshBasicMaterial({
    color: 0x6366f1,
    wireframe: true,
  });
  const torusKnot = new THREE.Mesh(geometry, material);
  scene.add(torusKnot);

  camera.position.z = 30;

  function animate() {
    requestAnimationFrame(animate);
    torusKnot.rotation.x += 0.01;
    torusKnot.rotation.y += 0.01;
    renderer.render(scene, camera);
  }

  animate();

  // Handle window resize
  window.addEventListener("resize", () => {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
  });
}

function typeEffect() {
  const text = "Hi 👋, I'm Alperen Gönül";
  let index = 0;
  const typingText = document.querySelector(".typing-text");

  function type() {
    if (typingText) {
      if (index < text.length) {
        (typingText as HTMLElement).style.visibility = "visible";
        typingText.innerHTML += text.charAt(index);
        index++;
        setTimeout(type, 100);
      }
    }
  }

  if (typingText) {
    typingText.innerHTML = "";
    type();
  }
}

function openVideo(url: string) {
  window.open(url, "_blank");
}
</script>

<style>
html {
  scroll-behavior: smooth;
}

#projects {
  background-color: #1f2937;
}

.wave-border {
  position: relative;
  width: 100%;
  overflow: hidden;
  line-height: 0;
  height: 150px; /* Ensure the height is set */
}

.wave-border svg {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 100%; /* Ensure the height is set */
}

.typing-text {
  visibility: hidden;
}

.contact-wave {
  transform: rotate(180deg);
  background-color: rgb(17 24 39 / var(--tw-bg-opacity, 1));
}

#contact {
  background-color: rgb(17 24 39 / var(--tw-bg-opacity, 1));
}

:root {
  --shade-100: #1f2937; /* Adjust this color as needed */
}

@media (max-width: 768px) {
  .container {
    padding-left: 1rem;
    padding-right: 1rem;
  }

  .text-5xl {
    font-size: 2.5rem;
  }

  .text-7xl {
    font-size: 3.5rem;
  }

  .text-xl {
    font-size: 1.25rem;
  }

  .text-2xl {
    font-size: 1.5rem;
  }

  .h-48 {
    height: 12rem;
  }

  .w-48 {
    width: 12rem;
  }

  .h-64 {
    height: 16rem;
  }

  .w-64 {
    width: 16rem;
  }

  .py-20 {
    padding-top: 5rem;
    padding-bottom: 5rem;
  }

  .mb-12 {
    margin-bottom: 3rem;
  }

  .mb-6 {
    margin-bottom: 1.5rem;
  }

  .mb-4 {
    margin-bottom: 1rem;
  }

  .mt-8 {
    margin-top: 2rem;
  }

  .mt-3 {
    margin-top: 0.75rem;
  }

  .px-6 {
    padding-left: 1.5rem;
    padding-right: 1.5rem;
  }

  .rounded-full {
    border-radius: 9999px;
  }

  .rounded-lg {
    border-radius: 0.5rem;
  }

  .rounded-t-lg {
    border-top-left-radius: 0.5rem;
    border-top-right-radius: 0.5rem;
  }

  .transition-colors {
    transition-property: background-color, border-color, color, fill, stroke;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
    transition-duration: 150ms;
  }

  .transition-opacity {
    transition-property: opacity;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
    transition-duration: 150ms;
  }

  .hover\:bg-blue-600:hover {
    background-color: #2563eb;
  }

  .hover\:bg-gray-700:hover {
    background-color: #374151;
  }

  .hover\:opacity-75:hover {
    opacity: 0.75;
  }

  .hover\:scale-110:hover {
    transform: scale(1.1);
  }

  .hover\:text-white:hover {
    color: #ffffff;
  }

  .hover\:underline:hover {
    text-decoration: underline;
  }

  .hover\:opacity-100:hover {
    opacity: 1;
  }

  .hover\:bg-gray-700:hover {
    background-color: #374151;
  }

  .hover\:text-white:hover {
    color: #ffffff;
  }
}
</style>
