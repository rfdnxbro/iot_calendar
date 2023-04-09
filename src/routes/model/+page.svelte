<script>
	import { onMount } from 'svelte'
	let aframe
	onMount(async () => {
		aframe = (await import('https://aframe.io/releases/1.4.0/aframe.min.js')).default
	})
  import cal from '$lib/images/calendar.png';
  import phone from '$lib/images/phone.png';
</script>

<a-scene>
  <a-assets>
    <img src={cal} id="calendar" />
    <img src={phone} id="phone" />
  </a-assets>
  <a-plane position="0 2 -4.2" rotation="0 0 0" width="200" height="200" color="#ccc"></a-plane>
  <a-plane position="0 -1 0" rotation="-90 0 0" width="200" height="200" color="#deb887"></a-plane>

  <a-plane position="0 2 -4" rotation="0 0 0" width="4" height="3.5" color="#fff" material="shader: flat; src: #calendar"></a-plane>
  <a-plane position="0 2 -4.1" rotation="0 0 0" width="4.4" height="4" color="#fff"></a-plane>

  <a-box position="1.5 -0.5 -3.9" rotation="-15 0 0" width="1.6" height="0.7" depth="0.1" color="#c66"></a-box>
  <a-plane width="0.6" height="1.2" position="1.5 -0.45 -3.8" rotation="-15 0 90" material="shader: flat; src: #phone"></a-plane>

  <a-box position="1.5 -1 -4.0" width="2" height="0.5" depth="0.3" color="#666"></a-box>

  <a-box position="0 -1 -4.3" width="5" height="2" depth="0.5" color="#333"></a-box>
  <a-sky color="#ECECEC"></a-sky>
</a-scene>
