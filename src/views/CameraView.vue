<template>
  <div>
    <video ref="video">Streming is unavialble</video>
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
    };
  },
};
</script>

<style></style>
