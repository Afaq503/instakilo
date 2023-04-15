<template>
  <div>
    <h2>This is Camera and now you click pic</h2>
    <video @canplay="initCanvas()" ref="video">Streming is unavialble</video>
    <button @click="takePicture()">Click Picture</button>
    <canvas ref="canvas" style="display: none" />
  </div>
</template>

<script>
export default {
  name: "camera",
  mounted() {
    this.video = this.$refs.video;
    this.canvas = this.$refs.canvas;
    this.startCapture();
  },
  methods: {
    startCapture() {
      navigator.mediaDevices
        .getUserMedia({ video: true, audio: false })
        .then((stream) => {
          this.video.srcObject = stream;
          this.video.play();
        })
        .catch((error) => {
          console.log(error);
        });
    },
    initCanvas() {
      this.canvas.setAttribute("width", this.video.videoWidth);
      this.canvas.setAttribute("height", this.video.videoHeight);
    },
    takePicture() {
      let context = this.canvas.getContext("2d");
      context.$emit("picture-taken", this.canvas.toDataUrl("image/png"));
    },
  },
  data() {
    return {
      video: null,
      canvas: null,
    };
  },
};
</script>

<style></style>
