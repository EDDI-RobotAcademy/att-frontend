<!-- src/components/UnityComponent.vue -->
<template>
  <div id="unity-container">
    <div id="unity-canvas"></div>
  </div>
</template>

<script>
export default {
  name: 'UnityComponent',
  mounted() {
    var buildUrl = "/Build";
    var loaderUrl = buildUrl + "/IF_TEST.loader.js";
    var config = {
        // dataUrl: `${buildUrl}/IF_TEST.data`,
        dataUrl: buildUrl + "/IF_TEST.data",
        frameworkUrl: buildUrl + "/IF_TEST.framework.js",
        codeUrl: buildUrl + "/IF_TEST.wasm",
        streamingAssetsUrl: "StreamingAssets",
        companyName: "DefaultCompany",
        productName: "IF",
        productVersion: "1.0",
    };

    const script = document.createElement('script');
    script.src = loaderUrl;
    script.onload = () => {
      createUnityInstance(document.querySelector("#unity-canvas"), config, (progress) => {
        console.log(`Loading: ${progress * 100}%`);
      }).then((unityInstance) => {
        this.unityInstance = unityInstance;
      }).catch((message) => {
        console.error(message);
      });
    };
    document.body.appendChild(script);
  },
  beforeUnmount() {
    if (this.unityInstance) {
      this.unityInstance.Quit();
    }
  }
};
</script>

<style scoped>
#unity-container {
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
}

#unity-canvas {
  width: 100%;
  height: 100%;
  outline: none;
}
</style>

<!-- <template>
  <div class="unity-container">
    <iframe src="/Unity.html" class="unity-frame"></iframe>
  </div>
</template>

<script>
export default {
  name: 'UnityComponent'
}
</script>

<style scoped>
.unity-container {
  display: flex;
  justify-content: center; /* 가로 중앙 정렬 */
  align-items: center; /* 세로 중앙 정렬 */
  margin-top: 35px;
  height: 605px;
}

.unity-frame {
  width: 96%;
  height: 100%;
  border: none;
}
</style> -->
