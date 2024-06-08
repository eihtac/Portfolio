<template>
  <BaseHeader/>
  <main>
    <section id="presentation">
      <h2 ref="txtAnim">Hello, World!</h2>
      <article>Je m'appelle Cathie, j'ai 25 ans et je suis en formation pour devenir développeuse web. Bienvenue sur mon Portfolio !</article>
      <div class="skills">
        <section class="competences">
          <h3>Compétences :</h3>
          <ul>
            <li><img src="../assets/img/html.png" alt="html 5"></li>
            <li><img src="../assets/img/css.png" alt="css 3"></li>
            <li><img src="../assets/img/js.png" alt="javascript"></li>
            <li><img src="../assets/img/vuejs.png" alt="vuejs"></li>
          </ul>
        </section>
        <section>
          <h3>Soft Skills :</h3>
          <ul>
            <li>Curiosité</li>
            <li>Patience</li>
            <li>Autonomie</li>
          </ul>
        </section>
      </div>
    </section> 
    <section id="projects">
      <h2>Projets</h2>
      <div class="desktop-view">
        <ul>
          <li @click="openModal('cv')" @mouseover="changeImage('cv')" @mouseout="resetImage">CV</li>
          <li @click="openModal('myHomeSpace')" @mouseover="changeImage('myHomeSpace')" @mouseout="resetImage">My home Space</li>
          <li @click="openModal('cahierDesCharges')" @mouseover="changeImage('cahierDesCharges')" @mouseout="resetImage">Cahier des charges</li>
          <li @click="openModal('espaceCommentaire')" @mouseover="changeImage('espaceCommentaire')" @mouseout="resetImage">Espace commentaire</li>
        </ul>
        <div class="project-image">
          <img :src="currentImage" alt="Photo du projet">
        </div>
      </div>
      <div class="mobile-view">
        <ul>
          <li>
            <div class="project-title">CV</div>
            <img src="../assets/img/cv.png" alt="CV">
          </li>
          <li>
            <div class="project-title">My home Space</div>
            <img src="../assets/img/MyHomeSpace.png" alt="My Home Space">
          </li>
          <li>
            <div class="project-title">Cahier des charges</div>
            <img src="../assets/img/cahier-des-charges.png" alt="Cahier des charges">
          </li>
          <li>
            <div class="project-title">Espace commentaire</div>
            <img src="../assets/img/espace-commentaire.png" alt="Espace commentaire">
          </li>
        </ul>
      </div>
    </section>
  </main>
  <BaseFooter :isHidden="isFooterHidden"/>
  <ModalWindow :isVisible="showModal" :projectName="selectedProjectName" @close="closeModal"/>
</template>

<script setup>
  import { ref, onMounted } from 'vue';
  import BaseHeader from "../components/BaseHeader.vue";
  import BaseFooter from "../components/BaseFooter.vue";
  import Typewriter from 'typewriter-effect/dist/core'; 
  import ModalWindow from "../components/ModalWindow.vue";

  const txtAnim = ref(null);
  const defaultImage = new URL('../assets/img/default.png', import.meta.url).href;
  const currentImage = ref(defaultImage);
  const showModal = ref(false);
  const selectedProjectName = ref('');
  const isFooterHidden = ref(false);

  onMounted(() => {
    new Typewriter(txtAnim.value, {
      loop: false
    })
    .typeString('Hello, World!')
    .start();
  });
  
  const changeImage = (projectName) => {
    switch (projectName) {
      case 'cv':
        currentImage.value = new URL('../assets/img/cv.png', import.meta.url).href;
        break;
      case 'myHomeSpace':
        currentImage.value = new URL('../assets/img/MyHomeSpace.png', import.meta.url).href;
        break;
      case 'cahierDesCharges':
        currentImage.value = new URL('../assets/img/cahier-des-charges.png', import.meta.url).href;
        break;
      case 'espaceCommentaire':
        currentImage.value = new URL('../assets/img/espace-commentaire.png', import.meta.url).href;
        break;
      default:
        currentImage.value = defaultImage;
    }
  };

  const resetImage = () => {
    currentImage.value = defaultImage;
  };

  const openModal = (projectName) => {
    selectedProjectName.value = projectName;
    showModal.value = true;
    isFooterHidden.value = true; 
  };

  const closeModal = () => {
    showModal.value = false;
    isFooterHidden.value = false;
  };
</script>

<style scoped>
  @font-face {
    font-family: 'share-tech-mono';
    src: url(../assets/fonts/ShareTechMono-Regular.woff);
    src: url(../assets/fonts/ShareTechMono-Regular.ttf) format('truetype');
  }

  #presentation {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  h2 {
    color: #FFD60A;
    font-size: 350%;
    margin-top: 130px;
    margin-bottom: 100px;
    font-family: 'share-tech-mono';
  }

  article {
    color: #FFE7B3;
    font-size: 130%;
  }

  .skills {
    display: flex;
    justify-content: space-evenly;
    width: 100%;
  }

  h3 {
    color: #FFD60A;
    margin-top: 100px;
    font-family: 'share-tech-mono';
    font-size: 150%;
  }

  .competences ul {
    display: flex;
    list-style-type: none;
    padding: 0;
  }

  li {
    color: #FFE7B3;
    font-size: 130%;
  }

  li img {
    width: 70px;
    margin: 5px;
  }

  #projects {
    margin-bottom: 200px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  #projects ul {
    list-style-type: none;
  }

  #projects li {
    font-size: 150%;
    cursor: pointer;
  }

  #projects li:hover {
    color: #FFD60A; 
  }

  .project-image {
    width: 100%;
    max-width: 800px;
    height: 700px; 
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden; 
    background-color: #0D141F; 
    margin-top: 20px;
  }

  .project-image img {
    max-width: 100%;
    max-height: 100%;
    object-fit: contain; 
    transition: opacity 0.3s; 
  }

  .desktop-view {
    display: flex;
    justify-content: space-evenly;
    width: 100%;
  }

  .mobile-view {
    display: none;
  }

  @media (max-width: 768px) {
    .desktop-view {
      display: none;
    }

    .mobile-view {
      display: block;
    }

    .mobile-view ul {
      list-style-type: none;
      padding: 0;
    }
  }
</style>