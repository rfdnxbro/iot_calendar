<script>
  import Canvas from '$lib/Canvas.svelte';
  const canvasHeight1 = 150;
  const canvasHeight2 = 400;
</script>

<div id="deviceArea">
  <div id="canvas1" style="height:{canvasHeight1}px">
    <Canvas canvasHeight={canvasHeight1} canvasTop={0} />
    <input type="number" min="1" max="12">月
    <input type="number" min="1" max="31">日
  </div>
  <div id="canvas2" style="height:{canvasHeight2}px">
    <Canvas canvasHeight={canvasHeight2} canvasTop={0} />
  </div>
</div>
<br>
<div id="button">
  <a href="../">&lt;　　</a>
</div>

<style>
#deviceArea {
  width: 360px;
  margin: 0 auto;
  font-size: 30px;
}
input {
  width: 200px;
  height: 60px;
  font-size: 60px;
  padding: 0 0 0 120px;
}
button {
  width: 100%;
  height: 60px;
}
#canvas1 {
  position: relative;
}
#canvas2 {
  border: 1px solid #000;
  position: relative;
  background: #fff;
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
