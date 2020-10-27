<template>
  <div
    class="progress-bar--container"
    :style="`${positionValue}; height: ${height}px`"
  >
    <div
      :style="`background-color: ${colorValue}; width: ${width}%;`"
      class="progress-bar"
    ></div>
  </div>
</template>
<script>
import { computed, ref, onMounted } from "vue";

export default {
  props: {
    color: {
      type: String,
      default: "#41B883",
    },
    position: {
      type: String,
      default: "top",
    },
    height: {
      type: String,
      default: "5",
    },
  },
  setup(props) {
    const width = ref(0);
    const colorValue = computed(() => props.color);
    const positionValue = computed(() => {
      let position = props.position;
      if (position === "top" || position === "bottom") {
        return `${position}: 0`;
      }
      return "top: 0";
    });

    function progress() {
      let documentHeight =
        document.documentElement.scrollHeight -
        document.documentElement.clientHeight;
      width.value = (window.scrollY * 100) / documentHeight;
    }
    onMounted(() => {
      document.addEventListener("scroll", function() {
        progress();
      });
    });

    return { colorValue, width, positionValue };
  }
};
</script>

<style lang="postcss">
.progress-bar--container {
  position: fixed;
  left: 0;
  right: 0;
  width: 100%;
}

.progress-bar {
  position: relative;
  width: 0;
  height: 100%;
  transition: width 0.1s ease;
}
</style>
