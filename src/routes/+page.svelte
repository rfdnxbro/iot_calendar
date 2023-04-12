<script>
  import Calendar from '$lib/Calendar.svelte';
  import Canvas from '$lib/Canvas.svelte';
</script>

<div id="relativeArea">
  <Calendar />
  <Canvas canvasHeight={800} canvasTop={100} />
</div>
<br>
<div id="button">
  <a href="./device">○</a>
</div>

<style>
#relativeArea {
  position: relative;
}
#button {
  text-align: center;
  font-size: 90px;
}
#button a {
  color: #000;
}
</style>
