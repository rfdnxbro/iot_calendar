<script>
  import Canvas from '$lib/Canvas.svelte';
  import { onMount } from 'svelte';

  const canvasHeight = 200;

  let month;
  let day;

  function numberClick(e) {
    const monthValue = month.value;
    const dayValue = day.value;
    const clickNumber = e.target.value;
    if (!monthValue || monthValue == 1) {
      setMonth(clickNumber, monthValue);
    } else if (!dayValue || dayValue <= 3) {
      setDay(clickNumber, dayValue);
    }
  }

  function setMonth(clickNumber, monthValue) {
    const newMonthValue = parseInt(monthValue * 10 + parseInt(clickNumber));
    if (newMonthValue <= 12) {
      month.value = newMonthValue;
    }
  }

  function setDay(clickNumber, dayValue) {
    const newDayValue = parseInt(dayValue * 10 + parseInt(clickNumber));
    if (newDayValue <= 31) { // 月問わず31日入れられるのは一旦無視
      day.value = newDayValue;
    }
  }
</script>

<div id="deviceArea">
  <input type="number" min="1" max="12" bind:this={month}>月
  <input type="number" min="1" max="31" bind:this={day}>日

  <div id="canvas" style="height:{canvasHeight}px">
    <Canvas canvasHeight={canvasHeight} canvasTop={0} />
  </div>

  <table>
    <tr>
      <td>
        <button on:click={numberClick} value="1">1</button>
      </td>
      <td>
        <button on:click={numberClick} value="2">2</button>
      </td>
      <td>
        <button on:click={numberClick} value="3">3</button>
      </td>
    </tr>
    <tr>
      <td>
        <button on:click={numberClick} value="4">4</button>
      </td>
      <td>
        <button on:click={numberClick} value="5">5</button>
      </td>
      <td>
        <button on:click={numberClick} value="6">6</button>
      </td>
    </tr>
    <tr>
      <td>
        <button on:click={numberClick} value="7">7</button>
      </td>
      <td>
        <button on:click={numberClick} value="8">8</button>
      </td>
      <td>
        <button on:click={numberClick} value="9">9</button>
      </td>
    </tr>
    <tr>
      <td>
      </td>
      <td>
        <button on:click={numberClick} value="0">0</button>
      </td>
      <td>
      </td>
    </tr>
  </table>
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
#canvas {
  border: 1px solid #000;
  position: relative;
}
#relativeArea {
  position: relative;
}
table {
  width: 100%;
}
</style>
