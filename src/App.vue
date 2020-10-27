<template>
  <header>
    <img src="@/assets/logo.png" alt="">
    <h2 v-text="dummyText.title"></h2>
    <ProgressBar :height="10" />
  </header>
  <div class="content" v-html="dummyText.content"></div>
</template>

<script>
import ProgressBar from "./components/ProgressBar.vue";
import dummyText from "./data/dummyText.json";

export default {
  name: "App",
  components: {
    ProgressBar,
  },
  data() {
    return {
      dummyText
    };
  },
};
</script>

<style lang="postcss">
html,
body {
  padding: 0;
  margin: 0;
}

#app {
  margin-top: 120px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

header {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  width: 100%;
  padding: 30px 10px 10px;
  background: #EEE;
}

img {
  max-width: 70px;
}

.content p {
  margin: 0 10px 1em;
  text-align: left;
}
</style>
