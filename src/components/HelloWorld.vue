<script setup>
import { ref } from "vue";

const count = ref(0);
function goTo(url) {
  window.location.href = url;
}
</script>

<template>
  <div id="app">
    <div>
      <h1>Oi!</h1>
      <div class="main">
        <p>My name is João Guilherme</p>
        <p>My email is me@joaoguilherme.me</p>
        <p>I'm a software engineer</p>
      </div>

      <div class="icons">
        <div>
          <div @click="goTo('https://www.linkedin.com/in/joaaogui/')">
            mdi-linkedin
          </div>
        </div>
        <div @click="goTo('https://github.com/joaaogui/')">mdi-github</div>
        <div @click="goTo('/youtube')">Youtube</div>
        <div @click="goTo('/spotify')">Spotify</div>
        <div @click="goTo('/imdb')">Imdb</div>
      </div>
    </div>
  </div>
</template>
<style></style>
