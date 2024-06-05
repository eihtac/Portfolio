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
  </main>
  <BaseFooter/>
</template>

<script setup>
  import { ref, onMounted } from 'vue';
  import BaseHeader from "../components/BaseHeader.vue";
  import BaseFooter from "../components/BaseFooter.vue";
  import Typewriter from 'typewriter-effect/dist/core'; 

  const txtAnim = ref(null);

  onMounted(() => {
    new Typewriter(txtAnim.value, {
      loop: false
    })
    .typeString('Hello, World!')
    .start();
  });
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
</style>