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
  <a href="./device">　　&gt;</a>
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
  border: 1px solid #000;
  padding: 0;
  margin: 0;
  background: #fff;
  border-radius: 20px;
}
#button a:hover {
  text-decoration: none;
}
</style>
