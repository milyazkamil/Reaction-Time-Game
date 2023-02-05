<template>
  <div class="main">
    <h1>Reaction Time Game</h1>
    <button class="play-btn" @click="startAll" :disabled="isDisabled">Play the Game</button>
  </div>
  <RedBox v-if="isWait && isPlaying == false" />
  <BlockVue :delay="delay" v-if="isPlaying" @stopTimer="stop" />
  <ResultsVue :millisecond="millisecond" v-if="isResult" @button="buttonAktive" />
  <FooterVue />
</template>

<script>
import BlockVue from './components/BlockVue.vue';
import RedBox from './components/RedBox.vue';
import ResultsVue from './components/ResultsVue.vue';
import FooterVue from './components/FooterVue.vue';
export default {
  name: 'App',
  data() {
    return {
      timer: null,
      delay: 2000 + (Math.random() * 5000),
      isPlaying: false,
      isResult: false,
      isDisabled: false,
      isWait: false,
      millisecond: 0,
    }
  },
  methods: {
    startAll() {
      this.start();
      this.isWait = true;
    },
    start() {
      this.isDisabled = true;
      this.isResult = false;
      this.timer = setInterval(() => {
        this.isPlaying = true;
        console.log(this.delay);
      }, this.delay);
    },
    stop(result) {
      clearInterval(this.timer);
      this.millisecond = result;
      this.isResult = true;
      this.isPlaying = false;
      this.isWait = false;
    },
    buttonAktive() {
      this.isDisabled = false;
    }
  },
  components: {
    BlockVue,
    RedBox,
    ResultsVue,
    FooterVue,
  }
}
</script>

<style>
* {
  -webkit-user-select: none; /* Safari */
  -ms-user-select: none; /* IE 10 and IE 11 */
  user-select: none; /* Standard syntax */
}
#app {
  font-family: 'Mochiy Pop One', sans-serif;
  text-align: center;
  margin-top: 40px;
  color: #000000;
}
.play-btn {
  width: 200px;
  height: 50px;
  border-radius: 10px;
  font-size: 20px;
  cursor: pointer;
  background-color: rgb(66, 222, 66);
  transition: all 0.6s;
  font-family: 'Mochiy Pop One', sans-serif;
}
.play-btn:hover {
  background-color: rgb(0, 255, 0);
  border-radius: 40px;
}

@media all and (max-width: 844px) {
  #app {
    margin-top: 20px;
  }
  .main {
    height: 15vh;
    margin-bottom: 5vh;
  }
  h1 {
    font-size: 30px;
    margin-bottom: 5vh;
  }
}

@media all and (max-width: 670px) {
  #app {
    margin-top: 10px;
  }
  .main {
    height: 15vh;
    margin-bottom: 0;
  }
  h1 {
    font-size: 25px;
    margin: 0;
    margin-bottom: 5px;
  }
}
</style>
