<template>
  <div class="camera-box">
    <div style="display: flex; justify-content: center">
      <img
        style="height: 25px"
        v-if="isCameraOpen"
        src="https://img.icons8.com/material-outlined/50/000000/camera--v2.png"
        class="button-img camera-shoot"
        @click="capture" />
      <div class="camera-button">
        <button
          type="button"
          class="button is-rounded cam-button"
          style="margin-left: 40%; background-color: white; border: 0px"
          @click="toggleCamera">
          <span v-if="!isCameraOpen"
            ><img
              style="height: 25px"
              class="button-img"
              src="https://img.icons8.com/material-outlined/50/000000/camera--v2.png"
          /></span>
          <span v-else
            ><img
              style="height: 25px"
              class="button-img"
              src="https://img.icons8.com/material-outlined/50/000000/cancel.png"
          /></span>
        </button>
      </div>
    </div>
    <div style="height: 200px">
      <div v-if="isCameraOpen" class="camera-canvas">
        <video
          ref="camera"
          :width="canvasWidth"
          :height="canvasHeight"
          autoplay></video>
        <canvas
          v-show="false"
          id="photoTaken"
          ref="canvas"
          :width="canvasWidth"
          :height="canvasHeight"></canvas>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Camera",
  components: {},
  data() {
    return {
      isCameraOpen: false,
      canvasHeight: 200,
      canvasWidth: 190,
      items: [],
    };
  },
};
</script>

<style scoped>
.camera-box {
  border: 1px dashed #d6d6d6;
  border-radius: 4px;
  padding: 2px;
  width: 80%;
  min-height: 300px;
}
</style>
