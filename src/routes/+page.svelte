<script lang="ts">
  import { onMount } from 'svelte';
  import 'aframe';
  import '@ar-js-org/ar.js/aframe/build/aframe-ar.js';

  onMount(() => {
    // Any additional setup can be done here
  });
</script>

<a-scene embedded arjs>
  <!-- Define a camera with AR.js capabilities -->
  <a-entity camera></a-entity>

  <!-- Define a 3D object (a simple box in this case) -->
  <a-box position="0 0.5 0" material="color: red;"></a-box>
</a-scene>
