<script setup lang="ts">
import { ref } from "vue";

const count = ref(0);
function goTo(url: string) {
  window.location.href = url;
}
</script>

<template>
  <div id="app">
    <div>
      <div>
        <div class="greeting">
          <h1>Oi!</h1>
        </div>
        <div class="main">
          <v-col cols="12">
            <p>My name is João Guilherme</p>
          </v-col>
          <v-col cols="12">
            <p>My email is me@joaoguilherme.me</p>
          </v-col>
          <v-col cols="12">
            <p>I'm a software engineer</p>
          </v-col>
        </div>

        <div class="icons">
          <div cols="6" style="text-align: end">
            <div>
              <div
                size="80"
                class="mr-2"
                @click="goTo('https://www.linkedin.com/in/joaaogui/')"
              >
                mdi-linkedin
              </div>
            </div>
          </div>
          <div cols="6" style="text-align: start">
            <div>
              <div size="80" @click="goTo('https://github.com/joaaogui/')">
                mdi-github
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style></style>
