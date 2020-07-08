<template>
  <v-app id="app">
    <v-main>
      <v-container fluid fill-height>
        <v-row class="greeting" align="start" no-gutters>
          <v-col>
            <h1>{{greeting}}</h1>
          </v-col>
        </v-row>
        <v-row class="main" align="center">
          <v-col cols="12">
            <p>
              My name is João Guilherme
            </p>
          </v-col>
          <v-col cols="12">
            <p>
              My email is me@joaoguilherme.me
            </p>
          </v-col>
          <v-col cols="12">
            <p>
              I'm a software engineer
            </p>
          </v-col>
        </v-row>

        <v-row class="icons" align="end">
          <v-col cols="6" style="text-align: end;">
            <v-hover v-slot:default="{ hover }">
              <v-icon size="80" class="mr-2" :color="hover ? 'blue' : 'black' "
                      @click="goTo('https://www.linkedin.com/in/joaaogui/')">mdi-linkedin
              </v-icon>
            </v-hover>
          </v-col>
          <v-col cols="6" style="text-align: start;">
            <v-hover v-slot:default="{ hover }">
              <v-icon size="80" :color="hover ? 'blue' : 'black' " @click="goTo('https://github.com/joaaogui/')">
                mdi-github
              </v-icon>
            </v-hover>
          </v-col>
        </v-row>
        <canvas class="canvas" @click="i()"></canvas>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    name: 'App',
    mounted() {
      this.startInterval()
      this.c = document.getElementsByTagName('canvas')[0]
      this.x = this.c.getContext('2d')
      this.pr = window.devicePixelRatio || 1
      this.w = window.innerWidth
      this.h = window.innerHeight
      this.f = 60
      this.r = 0
      this.u = this.m.PI * 2
      this.v = this.m.cos
      this.z = this.m.random
      this.c.width = this.w * this.pr
      this.c.height = this.h * this.pr
      this.x.scale(this.pr, this.pr)
      this.x.globalAlpha = 0.2
      this.i()
    },
    data: () => ({
      c: null,
      x: null,
      pr: null,
      w: null,
      h: null,
      f: null,
      q: null,
      m: Math,
      r: null,
      u: null,
      v: null,
      z: null,
      greeting: 'Hello',
      counter: 0,
      greetingsList: ["Hello", "Oi", "Hola", "Bonjour", "こんにちは", "Hallo", "你好", "Ciao", "Aloha", "Γεια σου", "नमस्ते"]
    }),
    methods: {
      startInterval() {
        setInterval(() => {
          this.greeting = this.greetingsList[this.counter]
          this.i()
          if (this.counter === this.greetingsList.length - 1) {
            this.counter = 0
          } else {
            this.counter += 1
          }
        }, 3000);
      },
      goTo(url) {
        window.location.href = url
      },
      i() {
        this.x.clearRect(0, 0, this.w, this.h)
        this.q = [{x: 0, y: this.h * .7 + this.f}, {x: 0, y: this.h * .7 - this.f}]
        while (this.q[1].x < this.w + this.f) this.d(this.q[0], this.q[1])
      },

      d(i, j) {
        this.x.beginPath()
        this.x.moveTo(i.x, i.y)
        this.x.lineTo(j.x, j.y)
        let k = j.x + (this.z() * 2 - 0.25) * this.f,
          n = this.y(j.y)
        this.x.lineTo(k, n)
        this.x.closePath()
        this.r -= this.u / -50
        this.x.fillStyle = '#' + (this.v(this.r) * 127 + 128 << 16 | this.v(this.r + this.u / 3) * 127 + 128 << 8 | this.v(this.r + this.u / 3 * 2) * 127 + 128).toString(16)
        this.x.fill()
        this.q[0] = this.q[1]
        this.q[1] = {x: k, y: n}
      },
      y(p) {
        let t = p + (this.z() * 2 - 1.1) * this.f
        return (t > this.h || t < 0) ? this.y(p) : t
      }

    }
  }
</script>

<style>
  .canvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    pointer-events: none;
  }

  .greeting {
    text-align: center;
    height: 25vh;
  }

  #app {
    font-family: 'Rubik', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    -webkit-font-smoothing: antialiased;
    color: #121314;
    text-align: center;
    overflow: hidden;
    margin: 0;
  }

  .main {
    overflow: hidden;
    z-index: 1;
    text-align: center;
    height: 50vh;
  }

  p {
    font-weight: 300;
    font-size: 2.0em;
  }

  h1 {
    font-size: 4.5em;
    font-weight: 500;
  }

  .icons {
    height: 25vh;
  }

</style>
