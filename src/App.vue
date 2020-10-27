<template>
  <header>
    <img src="@/assets/logo.png" alt="">
    <h2 v-text="title"></h2>
    <ProgressBar :height="10" />
  </header>
  <div class="content" v-html="content"></div>
</template>

<script>
import ProgressBar from "./components/ProgressBar.vue";
import {content, title } from "./data/dummyText.json";

export default {
  name: "App",
  components: {
    ProgressBar,
  },
  data() {
    return {
      content,
      title
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

.content {
  max-width: 1000px;
  margin: 0 auto;
}

p {
  margin-bottom: 1em;
  text-align: left;
}
</style>
