<script setup>
//https://github.com/Meqn/UnityWebGL.js
import { ref, onMounted, onBeforeUnmount } from "vue";
import UnityWebgl from "unity-webgl";
/*
  loaderUrl: "/Build/webglBuild.loader.js",
  dataUrl: "/Build/webglBuild.data",
  frameworkUrl: "/Build/webglBuild.framework.js",
  codeUrl: "/Build/webglBuild.wasm",
  */

const canvasRef = ref(null);
let unityComponent = null;

onMounted(() => {
  if (!unityComponent) {
    unityComponent = new UnityWebgl(canvasRef.value, {
      loaderUrl: "/Build/webglBuild.loader.js",
      dataUrl: "/Build/webglBuild.data",
      frameworkUrl: "/Build/webglBuild.framework.js",
      codeUrl: "/Build/webglBuild.wasm",
    });
  }
});
onBeforeUnmount(() => {
  if (unityComponent) {
    unityComponent.destroy();
    unityComponent = null;
  }
});
</script>
<script>
export default {
  name: "HomeView",
  components: {},
  mounted() {
    console.log("## mounted");
  },
};
</script>
<template>
  <div style="width: 800px; height: 600px; border: 1px solid #f00">
    <canvas id="canvas" ref="canvasRef" style="width: 100%; height: 100%" />
  </div>
</template>
