<template>
  <v-app>
    <v-main>
      <v-container fluid>
        <h1 class="greeting">{{greeting}}</h1>
        <div class="main">
          <p>
            My name is João Guilherme
          </p>
          <p>
            My email is me@joaoguilherme.me
          </p>
          <p>
            I'm a software engineer
          </p>
          <p>
            <v-icon @click="goTo('https://www.linkedin.com/in/joaaogui/')">mdi-linkedin</v-icon>
            <v-icon @click="goTo('https://github.com/joaaogui/')">mdi-github</v-icon>
          </p>

        </div>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    name: 'App',
    mounted() {
      this.startInterval()
    },
    data: () => ({
      greeting: 'Hello',
      counter: 0,
      greetingsList: ["Hello", "Oi", "Hola", "Bonjour", "こんにちは", "Hallo", "你好", "Ciao", "Aloha", "Γεια σου", "नमस्ते"]
    }),
    methods: {
      startInterval() {
        setInterval(() => {
          this.greeting = this.greetingsList[this.counter]
          if (this.counter === this.greetingsList.length - 1) {
            this.counter = 0
          } else {
            this.counter += 1
          }
        }, 1000);
      },
      goTo(url) {
        window.location.href = url
      }
    }
  }
</script>
