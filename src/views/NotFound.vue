<template>
  <BaseHeader class="nopadding"/>
  <div class="notfound">
    <h1>404 - Page non trouvée !</h1>
    <img src="@/assets/img/lighthouse.png" alt="Phare"/>
    <article>Oups ! Il semble que vous vous soyez égaré. <br>
    <router-link to="/">Retourner à l'accueil</router-link>.</article>
  </div>
  <BaseFooter class="nopadding"/>
</template>
  
<script setup>
  import BaseHeader from '@/components/BaseHeader.vue';
  import BaseFooter from '@/components/BaseFooter.vue';
</script>
  
<style scoped>
  .nopadding{
    padding: 0;
  }

  .notfound{
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  h1{
    color: #FFD60A;
    padding-top: 100px;
    padding-bottom: 20px;
  }

  img{
    width: 40%;
  }

  article {
    color: #FFE7B3
  }

  a{
    color: #FFE7B3
  }

  a:hover{
    color: #FFD60A
  }
</style>
  