<template>
  <div>
  </div>
</template>

<script>
import THREE from './three';

export default {
  name: 'Logo3D',

  data() {
    return {
      scene: null,
      camera: null,
      renderer: null
    }
  },

  methods: {
    animate: function () {
      this.render();
      requestAnimationFrame(this.animate);
    },

    render: function () {
      this.renderer.render(this.scene, this.camera);
    }
  },

  mounted() {
    this.scene = new THREE.Scene();

    this.camera = new THREE.PerspectiveCamera(2, window.innerWidth / window.innerHeight, 0.01, 1000);
    this.camera.position.set(-5, -5, 20);

    this.renderer = new THREE.WebGLRenderer({ alpha: true });
    this.renderer.setClearColor(0xffffff);
    this.renderer.setPixelRatio(window.devicePixelRatio);
    this.renderer.setSize(window.innerWidth, window.innerHeight);
    document.body.appendChild(this.renderer.domElement);

    new THREE.OrbitControls(
      this.camera,
      this.renderer.domElement);
      
    var ambientLight = new THREE.AmbientLight(0xcccccc);
    this.scene.add(ambientLight);

    var directionalLight = new THREE.DirectionalLight(0xffffff);
    directionalLight.position.set(0, 1, 1).normalize();
    this.scene.add(directionalLight);

    var loader = new THREE.GLTFLoader();
    var that = this;

    loader.load('/logo_vue.glb', function (gltf) {

      gltf.scene.scale.set(2, 2, 2);
      gltf.scene.position.x = 0;
      gltf.scene.position.y = 0;
      gltf.scene.position.z = 0;

      that.scene.add(gltf.scene);
    });

    this.render();
    this.animate();
  }
};
</script>

<style scoped>
body {
  margin: 0;
}
canvas {
  width: 100%;
  height: 100%;
}
</style>
