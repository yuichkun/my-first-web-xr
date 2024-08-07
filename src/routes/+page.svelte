<script lang="ts">
	import '@google/model-viewer';
</script>

<div class="container">
	<model-viewer src="/model.glb" autoplay auto-rotate class="viewer" ar>
		<button slot="ar-button" class="ar-button"> 🍴部屋に置いてみる </button>
	</model-viewer>
</div>

<style>
	.container {
		width: 100vw;
		height: 80vh;
	}
	.viewer {
		width: 100%;
		height: 100%;
	}
	.ar-button {
		position: fixed;
		bottom: 12px;
		right: 12px;
		padding: 32px;
		border-radius: 32px;
		font-size: 62px;
		text-align: center;
		background: #ffbf47;
		color: white;
		font-weight: bold;
	}
</style>
