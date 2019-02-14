<template>
  <div id="app">
    <h2 v-if="showCountdown"><a href="https://www.vuejs.amsterdam/" class="amsterdam">#VuejsAmsterdam</a> will start in  {{countdown}}</h2>
    <h4>Made with <a class="amsterdam" href="https://threejs.org/">three.js</a>, so, yes, you can move the 3D logo ;-)</h4>
    <Logo3D />
  </div>
</template>

<script>
import Logo3D from './components/Logo3D.vue';

export default {
  name: 'app',

  components: {
    Logo3D
  },

  data() {
    return {
      countdown: this.getCountdown(),
      showCountdown: false
    }
  },

  mounted() {
    if (this.showCountdown) {
      setInterval(this.updateCountdown, 1000);
    }
  },

  methods: {
    updateCountdown: function () {
      this.countdown = this.getCountdown();
    },

    getCountdown: function () {
      const now = new Date();
      // Vuejs Amsterdam start date
      const startDate = new Date(2019, 1, 13, 9);
      let diff = (startDate - now) / 1000;
      console.log(diff)

      const days = Math.floor(diff / (3600 * 24));
      diff -= days * 3600 * 24;

      const hours = Math.floor(diff / 3600);
      diff -= hours * 3600;

      const min = Math.floor(diff / 60);
      diff -= min * 60;

      const buffer = [];
      if (days > 0) buffer.push(days + ' day(s)');
      if (days > 0 || hours > 0) buffer.push(hours + ' hour(s)');
      if (days > 0 || hours > 0 || min > 0) buffer.push(min + ' minute(s)');
      if (days > 0 || hours > 0 || min > 0 || diff > 0) buffer.push(Math.floor(diff) + ' second(s)');

      return buffer.join(' ');
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin-left: 60px;
  margin-right: auto;
}

.amsterdam {
  color: #FF691F;
}
</style>
