<template>
  <div id="app">
    <vue-plyr
      ref="plyr2"
      :options="{ controls: [''] }"
      class="full"
      :class="{ hide: !hideVideo1 }"
    >
      <video preload="auto">
        <source
          src="http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ForBiggerFun.mp4"
          type="video/mp4"
          size="1080"
        />
      </video>
    </vue-plyr>

    <vue-plyr
      ref="plyr"
      :options="{ controls: [''] }"
      :class="{ hide: hideVideo1 }"
      class="full"
    >
      <video preload="auto">
        <source
          src="http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"
          type="video/mp4"
          size="1080"
        />
      </video>
    </vue-plyr>

    <div class="bottom flex">
      <button @click="$refs.plyr.player.play()">PLAY</button>
      <button @click="$refs.plyr.player.pause()">PAUSE</button>
      <button @click="$refs.plyr.player.currentTime = 25">Segon 25</button>

      <button @click="changeVideo">VIDEO 2</button>
    </div>

    <p>{{ seeked }}</p>
  </div>
</template>

<script>
export default {
  name: "app",
  components: {
    // HelloWorld
  },
  data: function() {
    return {
      counter: 0,
      seeked: "",
      hideVideo1: false
    };
  },
  methods: {
    changeVideo() {
      this.$refs.plyr.player.stop();
      this.$refs.plyr.player.destroy();

      this.seeked = this.$refs.plyr2.player.buffered;

      this.hideVideo1 = true;

      this.$refs.plyr2.player.play();
    }
  },
  mounted() {}
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
}

.full {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.hide {
  display: none;
}

.block {
  display: block;
}

.absolute {
  display: absolute;
}

.bottom {
  position: absolute;
  bottom: 0;
}

.flex {
  display: flex;
}

button {
  background-color: black;
  color: white;
  margin: 1rem;
  padding: 1rem 2rem;
  border-radius: 3rem;
  border: none;
}

button:active {
  opacity: 0.7;
}
</style>