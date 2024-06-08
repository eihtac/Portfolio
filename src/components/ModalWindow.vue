<template>
    <div class="modal" v-if="isVisible" @click.self="close">
        <div class="modal-content">
            <span class="close" @click="close">&times;</span>
            <h2>Zoom sur le projet {{ modalTitle }} :</h2>
            <div class="modal-body">
                <div v-if="projectName === 'cv'">
                    <article>Créé le <time datetime="2024-03-04">04.03.2024</time> avec <img src="../assets/img/html.png" alt="html"> et <img src="../assets/img/css.png" alt="css">. <br>
                    Vous pouvez voir le projet <a target="_blank" href="/creer-un-cv-en-ligne/index.html">en cliquant ici</a> ou voir le repository github : <a target="_blank" href="https://github.com/eihtac/devoir-cv"><img src="../assets/img/github2.png" alt="icone github"></a>.</article>
                    <img src="../assets/img/cv.png" alt="Photo du projet cv">
                </div>
                <div v-if="projectName === 'myHomeSpace'">
                    <article>Créé le <time datetime="2024-03-15">15.03.2024</time> avec <img src="../assets/img/html.png" alt="html"> et <img src="../assets/img/css.png" alt="css">. <br>
                    Vous pouvez voir le projet <a target="_blank" href="/my-home-space/index.html">en cliquant ici</a> ou voir le repository github : <a target="_blank" href="https://github.com/eihtac/my-home-space"><img src="../assets/img/github2.png" alt="icone github"></a>.</article>
                    <img src="../assets/img/MyHomeSpace.png" alt="Photo du projet My Home Space">
                </div>
                <div v-if="projectName === 'cahierDesCharges'">
                    <article>Créé le <time datetime="2024-03-31">31.03.2024</time>. <br>
                    Vous pouvez voir le projet <a target="_blank" href="/cahier-des-charges.pdf">en cliquant ici</a>.</article>
                    <img src="../assets/img/cahier-des-charges.png" alt="Photo du projet cahier des charges">
                </div>
                <div v-if="projectName === 'espaceCommentaire'">
                    <article>Créé le <time datetime="2024-04-26">26.04.2024</time> avec <img src="../assets/img/js.png" alt="Javascript">. <br>
                    Vous pouvez voir le projet <a target="_blank" href="/dynamiser-un-espace-commentaire/index.html">en cliquant ici</a> ou voir le repository github : <a target="_blank" href="https://github.com/eihtac/espace-commentaire"><img src="../assets/img/github2.png" alt="icone github"></a></article>
                    <img src="../assets/img/espace-commentaire.png" alt="Photo du projet espace commentaire">
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
    import { computed } from 'vue';
    
    const props = defineProps({
        isVisible: {
            type: Boolean,
            required: true
        },
        projectName: {
            type: String,
            required: true
        }
    });

    const emit = defineEmits(['close']);

    const close = () => {
        emit('close');
    };

    const modalTitle = computed(() => {
        switch (props.projectName) {
            case 'cv':
                return 'CV';
            case 'myHomeSpace':
                return 'My Home Space';
            case 'cahierDesCharges':
                return 'Cahier des charges';
            case 'espaceCommentaire':
                return 'Espace commentaire';
            default:
                return '';
        }
    });
</script>

<style scoped>
    .modal{
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: rgba(0, 0, 0, 0.8);
    }

    .modal-content{
        background-color: #111A27;  
        width: 80%; 
        position: relative;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        max-height: 90vh;
        overflow-y: auto;
    }

    .modal-body{
        max-height: calc(90vh - 80px);
    }

    span{
        color: #FFD60A;
        font-size: 28px;
        position: absolute; 
        top: 10px; 
        right: 10px; 
    }

    span:hover{
        color: #FFE7B3;
        cursor: pointer;
    }

    h2{
        color: #FFCA16;
        padding-top: 20px;
    }

    article{
        color: #FFE7B3;
        text-align: center; 
    }

    article img {
        width: 40px;
    }

    img{
        height: 10%;
        margin-top: 10px; 
    }

    a {
        text-decoration: none;
        color: #FFCA16;
    }
</style>