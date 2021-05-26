<template>
  
  <div id="container">
      
  </div>
</template>
<script>
import * as THREE from 'three'


export default {

  name: 'Canva',
  data() {
    return {
      cube: null,
      renderer: null,
      scene: null,
      camera: null
    }
  },
  methods: {
    init: function() {
      this.scene = new THREE.Scene()
      this.camera = new THREE.PerspectiveCamera(
        75,
        window.innerWidth / window.innerHeight,
        0.1,
        100
      )

      this.renderer = new THREE.WebGLRenderer()
      this.renderer.setSize(window.innerWidth, window.innerHeight)
      document.body.appendChild(this.renderer.domElement)

      const geometry = new THREE.BoxGeometry(1, 1, 1)
      const material = new THREE.MeshBasicMaterial({ color: 0xDE6100  })
      this.cube1 = new THREE.Mesh(geometry, material)
      this.scene.add(this.cube1)
      
      
    this.cube2 = new THREE.Mesh(geometry, material)
    this.scene.add(this.cube2)
      
      
      this.cube2.position.x-=5

      this.cube1.position.x+=5
      this.camera.position.z = 5

      
    },
    animate: function() {
      requestAnimationFrame(this.animate)

      this.cube1.rotation.x += 0.01
      this.cube1.rotation.y += 0.01
      this.cube2.rotation.x += 0.02
      this.cube2.rotation.y += 0.01

      this.renderer.render(this.scene, this.camera)
    }
  },
  mounted() {
    this.init()
    this.animate()
  }
}
</script>

