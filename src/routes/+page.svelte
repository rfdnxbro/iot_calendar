<script>
  import Calendar from '$lib/Calendar.svelte';
  import { onMount } from 'svelte';

  let canvas;
  let wrapper;

  onMount(() => {
    const context = canvas.getContext('2d');
    let isDrag = false;

    function draw(x, y) {
      if(!isDrag) {
        return;
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
      canvas.addEventListener('mousemove', (event) => {
        draw(event.offsetX, event.offsetY);
      });
      canvas.setAttribute('width', wrapper.offsetWidth);
    }

    initEventHandler();
  });
</script>

<Calendar />
<div id="wrapper" bind:this={wrapper}>
  <canvas id="canvas" bind:this={canvas} height="800"></canvas>
</div>

<style>
#canvas {
  /* background: rgba(255, 255, 255, 0.2); */
}
#wrapper {
  position: absolute;
  width: 100%;
  height: 800px;
  top: 100px;
  left: 0;
}
</style>
