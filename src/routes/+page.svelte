<script>
	import AFRAME from 'aframe';
	// import '@ar-js-org/ar.js/aframe/build/aframe-ar.js';
	import { tapPlaceComponent } from '../lib/tap-place';
	AFRAME.registerComponent('tap-place', tapPlaceComponent);
</script>

<div class="container">
	<div class="over">
		<span id="promptText">Tap To Place Model</span>
	</div>

	<a-scene
		tap-place
		landing-page
		xrextras-loading
		xrextras-runtime-error
		renderer="colorManagement:true"
		xrweb="
    allowedDevices: any;
    defaultEnvironmentFogIntensity: 0.5;
    defaultEnvironmentFloorTexture: #groundTex;
    defaultEnvironmentFloorColor: #FFF;
    defaultEnvironmentSkyBottomColor: #B4C4CC;
    defaultEnvironmentSkyTopColor: #5ac8fa;
    defaultEnvironmentSkyGradientStrength: 0.5;"
	>
		<!-- We can define assets here to be loaded when A-Frame initializes -->
		<a-assets>
			<!-- <img id="groundTex" src="assets/sand.jpg" /> -->
			<a-asset-item id="cactusModel" src="model.glb"></a-asset-item>
		</a-assets>

		<!-- The raycaster will emit mouse events on scene objects specified with the cantap class -->
		<a-camera
			id="camera"
			position="0 8 8"
			raycaster="objects: .cantap"
			cursor="
      fuse: false;
      rayOrigin: mouse;"
		>
		</a-camera>

		<a-entity
			light="
      type: directional;
      intensity: 0.8;
      castShadow: true;
      shadowMapHeight:2048;
      shadowMapWidth:2048;
      shadowCameraTop: 40;
      shadowCameraBottom: -40;
      shadowCameraRight: 40;
      shadowCameraLeft: -40;
      target: #camera"
			xrextras-attach="target: camera; offset: 8 15 4"
			position="1 4.3 2.5"
			shadow
		>
		</a-entity>

		<a-light type="ambient" intensity="0.5"></a-light>

		<!-- Adding the cantap class allows the ground to be clicked -->
		<a-box
			id="ground"
			class="cantap"
			scale="1000 2 1000"
			position="0 -0.99 0"
			material="shader: shadow; transparent: true; opacity: 0.4"
			shadow
		>
		</a-box>
	</a-scene>
</div>

<style>
	.container {
		margin: 0;
		overflow: hidden;
	}
	.over {
		z-index: 10;
		pointer-events: none;
		position: absolute;
		top: 0;
		left: 0;
		bottom: 0;
		right: 0;

		text-align: center;
		color: white;
		font-family: 'Nunito', monospace;
		text-shadow: 0px 0px 5px black;
	}
	#promptText {
		font-size: 2em;
		bottom: 12vh;
		position: absolute;
		left: 50%;
		transform: translate(-50%, 0);
	}
</style>
