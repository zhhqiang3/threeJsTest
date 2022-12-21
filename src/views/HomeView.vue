<script setup>
  import * as THREE from "three";
// 定义场景
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(
    75,
    window.innerWidth / window.innerHeight,
    1,
    500
  );
  camera.position.set( 0, 0, 50 );
  camera.lookAt(new THREE.Vector3(0,0,10));

  const renderer = new THREE.WebGLRenderer();
  renderer.setSize(window.innerWidth, window.innerHeight);
  document.body.appendChild(renderer.domElement);
// 场景定义完毕

const material = new THREE.LineBasicMaterial( { color: 0x0000ff } );
const points = [];
points.push( new THREE.Vector3( 0, 0, 0 ) );
points.push( new THREE.Vector3( - 10, 0, 0 ) );
points.push( new THREE.Vector3( 0, 10, 0 ) );
points.push( new THREE.Vector3( 10, 0, 0 ) );
points.push( new THREE.Vector3( 0, 0, 0 ) );
points.push( new THREE.Vector3( 0, 10, 0 ) );
points.push( new THREE.Vector3( 0, 10, 20 ) );
points.push( new THREE.Vector3( 0, 0, 20 ) );
points.push( new THREE.Vector3( - 10, 0, 20 ) );
points.push( new THREE.Vector3( 0, 10, 20 ) );
points.push( new THREE.Vector3( 10, 0, 20 ) );
points.push( new THREE.Vector3( 0, 0, 20 ) );

const geometry = new THREE.BufferGeometry().setFromPoints( points );

const line = new THREE.Line( geometry, material );
scene.add(line);
renderer.render( scene, camera );

// // 画个方块
  const geometry_cube = new THREE.BoxGeometry(5, 5, 5);
  const material_cube = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
  const cube = new THREE.Mesh(geometry_cube, material_cube);
  scene.add(cube);

  // camera.position.z = 20;
// // 动画
  function animate() {
    requestAnimationFrame(animate);

    // cube.rotation.x += 0.01;
    cube.rotation.y += 0.01;

    // line.rotation.x += 0.01;
    line.rotation.y += 0.01;

    renderer.render(scene, camera);
  }
renderer.render(scene, camera);
  animate();
</script>

<template>
  <main></main>
</template>
