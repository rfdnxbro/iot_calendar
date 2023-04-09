<script>
  import Calendar from '$lib/Calendar.svelte';
  import Canvas from '$lib/Canvas.svelte';
</script>

<div id="relativeArea">
  <Calendar />
  <Canvas canvasHeight={800} canvasTop={100} />
</div>

<style>
#relativeArea {
  position: relative;
}
</style>
