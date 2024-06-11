<template>
  <div class="contact-form">
    <form @submit.prevent="submitForm" action="https://formspree.io/f/xoqggjdy" method="POST">
      <div>
        <label for="name">Nom/Prénom</label>
        <input type="text" v-model="name" name="name" id="name" required>
      </div>
      <div>
        <label for="subject">Objet</label>
        <input type="text" v-model="subject" name="subject" id="subject" required>
      </div>
      <div>
        <label for="message">Message</label>
        <textarea v-model="message" name="message" id="message" required></textarea>
      </div>
      <button type="submit">Envoyer</button>
    </form>
    <div class="success-message" v-if="successMessage">{{ successMessage }}</div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const name = ref('');
const subject = ref('');
const message = ref('');
const successMessage = ref('');

const submitForm = async (event) => {
  event.preventDefault();

  const form = event.target;
  const formData = new FormData(form);

  try {
    const response = await fetch(form.action, {
      method: 'POST',
      body: formData,
      headers: {
        'Accept': 'application/json'
      }
    });

    if (response.ok) {
      successMessage.value = 'Votre message a bien été envoyé !';
      name.value = '';
      subject.value = '';
      message.value = '';
    } else {
      const result = await response.json();
      successMessage.value = result.errors ? result.errors.map(error => error.message).join(", ") : "Erreur lors de l'envoi du message. Veuillez réessayer.";
    }
  } catch (error) {
    successMessage.value = `Erreur lors de l'envoi du message : ${error.message}. Veuillez réessayer.`;
  }
};
</script>

<style scoped>
.contact-form {
  max-width: 600px;
  margin: auto;
  padding-bottom: 100px;
}

.contact-form div {
  margin-bottom: 3em;
}

.contact-form label {
  color: #FFD60A;
  display: block;
  margin-bottom: 0.5em;
}

.contact-form input, .contact-form textarea {
  width: 100%;
  padding: 0.5em;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.contact-form button {
  padding: 0.75em 1.5em;
  border: none;
  border-radius: 4px;
  background-color: #0D141F;
  color: #FFD60A;
  cursor: pointer;
}

.contact-form button:hover {
  color: #FFE7B3;
}

.success-message {
  padding-top: 50px;
  color: #FFD60A;
}
</style>
