<script setup>
  import * as THREE from "three";
// 定义场景
  const scene = new THREE.Scene();
  const fog = new THREE.Fog({color: 'red'});
  scene.fog = fog;
  
  const camera = new THREE.PerspectiveCamera(
    75,
    window.innerWidth / window.innerHeight,
    1,
    500
  );
  camera.position.set( 0, 0, 20 );
  camera.lookAt(new THREE.Vector3(0,0,10));

  const renderer = new THREE.WebGLRenderer();
  renderer.setSize(window.innerWidth, window.innerHeight);
  document.body.appendChild(renderer.domElement);
// 场景定义完毕

const texture = new THREE.TextureLoader().load( "http://lingling.ccooddee.cn/20180810072204_32893.jpg" );
texture.wrapS = THREE.RepeatWrapping;
texture.wrapT = THREE.RepeatWrapping;
texture.repeat.set( 4, 4 );


const geometry = new THREE.BoxGeometry( 10, 10, 10 );
const material = new THREE.MeshBasicMaterial( { color: 0x00ffff, map:texture,fog:true, reflectivity:0.5 } );
const cube = new THREE.Mesh( geometry, material );
scene.add( cube );


// scene.add(texture)
// // 动画
  function animate() {
    requestAnimationFrame(animate);

    cube.rotation.x += 0.01;
    cube.rotation.y += 0.01;

    // // line.rotation.x += 0.01;
    // line.rotation.y += 0.01;

    renderer.render(scene, camera);
  }
renderer.render(scene, camera);
  animate();
</script>

<template>
  <main><div id="info">Description</div></main>
</template>

<style scoped>
#info {
	position: absolute;
	top: 10px;
	width: 100%;
	text-align: center;
	z-index: 100;
	display:block;
}
</style>