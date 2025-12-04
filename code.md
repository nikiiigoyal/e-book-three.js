# Starting code scene,camera,renderer,animate function

_import * as THREE from "three";
**let canvas**= document.getElementById("#threejs")
**let scene** = new THREE.Scene();
**let camera** = new THREE.PerspectiveCamera(30,window.innerWidth/window.innerHeight,1,1000);
camera.position.set( 0, 400, 700 );
console.log("Camera Position (x, y, z):", camera.position.x, camera.position.y, camera.position.z);
**const renderer** = new THREE.WebGLRenderer({ canvas: canvas, antialias: true });
renderer.setPixelRatio(window.devicePixelRatio);
renderer.setSize(window.innerWidth, window.innerHeight);
renderer.setAnimationLoop(animate)
**function animate**() {
  renderer.render(scene,camera)
}

