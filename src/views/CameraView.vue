<template>
  <div>
    <h2>This is Camera and now you click pic</h2>
    <video ref="video">Streming is unavialble</video>
    <canvas ref="canvas" style="display: none" />
  </div>
</template>

<script>
export default {
  name: "camera",
  mounted() {
    this.video = this.$refs.video;
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
