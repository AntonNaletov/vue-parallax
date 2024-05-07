<template>
  <div class="page">
    <img alt="Head_01" src="../assets/Head_01.jpg">
    <img alt="Head_03" src="../assets/Head_03.jpg">
    <canvas id="canvas" style="width: 100%; height: 100%; display: block;"></canvas>
  </div>
</template>

<script>
export default {
  name: 'FirstPage',
  data() {
    return {
      showSpinners: 'true',
    }
  },
  computed: {

  },
  created() {
    console.log('123')
    const canvas = document.getElementById("canvas");
    const gl = canvas.getContext("webgl");
    if (!gl) {
      return
    }
    let originalImage = { width: 1, height: 1 }; // replaced after loading
    const originalTexture = twgl.createTexture(gl, {
      src: "../assets/Head_01.jpg",
      crossOrigin: '',
    }, (err, texture, source) => {
      originalImage = source;
    })
    const mapTexture = twgl.createTexture(gl, {
      src: "../assets/Head_03.jpg", crossOrigin: '',
    });
    const programInfo = twgl.createProgramInfo(gl, ["vs", "fs"]);
    console.log(programInfo)
    console.log(mapTexture)
    console.log(originalTexture)
    console.log(twgl)
  }
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.page img {
  width: 100%;
}
</style>
