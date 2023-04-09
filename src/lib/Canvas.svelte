<script>
  import { onMount } from 'svelte';
  export let canvasHeight;
  export let canvasTop;

  let canvas;
  let wrapper;

  onMount(() => {
    const context = canvas.getContext('2d');
    let isDrag = false;

    function draw(event) {
      if(!isDrag) {
        return;
      }
      let x, y;
      if (event.touches) { // touchイベント
        event.preventDefault(); // ページ引っ張られるのを防ぐ
        const offset = canvas.getBoundingClientRect();
        x = event.touches[0].pageX - offset.left;
        y = event.touches[0].pageY - offset.top;
      } else {
        x = event.offsetX;
        y = event.offsetY;
      }

      context.lineTo(x, y);
      context.stroke();
    }

    function dragStart(event) {
      context.beginPath();
      isDrag = true;
    }
    function dragEnd(event) {
      context.closePath();
      isDrag = false;
    }

    function initEventHandler() {
      canvas.addEventListener('mousedown', dragStart);
      canvas.addEventListener('mouseup', dragEnd);
      canvas.addEventListener('mouseout', dragEnd);
      canvas.addEventListener('touchstart', dragStart);
      canvas.addEventListener('touchend', dragEnd);
      canvas.addEventListener('touchcancel', dragEnd);
      canvas.addEventListener('mousemove', (event) => {
        draw(event);
      });
      canvas.addEventListener('touchmove', (event) => {
        draw(event);
      });
      canvas.setAttribute('width', wrapper.offsetWidth);
    }

    initEventHandler();
  });
</script>

<div id="wrapper" bind:this={wrapper} style="height:{canvasHeight}px;top:{canvasTop}px;">
  <canvas id="canvas" bind:this={canvas} height={canvasHeight}></canvas>
</div>

<style>
#canvas {
  /* background: rgba(255, 255, 255, 0.2); */
}
#wrapper {
  position: absolute;
  width: 100%;
  left: 0;
}
</style>
