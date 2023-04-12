<script>
  let today = new Date();
  let currentMonth = today.getMonth();
  let currentYear = today.getFullYear();

  function generateCalendar(month, year) {
    const firstDay = (new Date(year, month)).getDay();
    let date = 1;
    const daysInMonth = 32 - new Date(year, month, 32).getDate();

    const weeks = [];
    for (let i = 0; i < 6; i++) {
      const days = [];
      for (let j = 1; j < 8; j++) {
        if (i === 0 && j < firstDay || date > daysInMonth) {
          days.push('');
        } else {
          days.push(date);
          date++;
        }
      }
      weeks.push(days);
    }
    return weeks;
  }

  let weeks = generateCalendar(currentMonth, currentYear);

  function nextMonth() {
    currentMonth = (currentMonth + 1) % 12;
    if (currentMonth === 0) {
      currentYear++;
    }
    weeks = generateCalendar(currentMonth, currentYear);
  }

  function prevMonth() {
    if (currentMonth === 0) {
      currentMonth = 11;
      currentYear--;
    } else {
      currentMonth--;
    }
    weeks = generateCalendar(currentMonth, currentYear);
  }
</script>

<style>
  table {
    border-collapse: collapse;
    width: 100%;
  }
  th, td {
    border: 1px solid #ccc;
    padding: 8px;
    text-align: center;
  }
  td {
    height: 100px;
    vertical-align: top;
  }
  th {
    background-color: #f2f2f2;
  }
  button {
    cursor: pointer;
    font-size: 60px;
    border-radius: 20px;
    background: #fff;
    border: 1px solid #000;
  }
  #thisMonth {
    font-size: 40px;
    padding: 0 10px;
  }
  .center {
    text-align: center;
  }
  .sat {
    color: #00f;
  }
  .sun {
    color: #f00;
  }
</style>

<div class="center">
  <button on:click={prevMonth}>&lt;</button>
  <span id="thisMonth">{currentYear}年{currentMonth + 1}月</span>
  <button on:click={nextMonth}>&gt;</button>
</div>

<table>
  <thead>
    <tr>
      <th>月</th>
      <th>火</th>
      <th>水</th>
      <th>木</th>
      <th>金</th>
      <th class="sat">土</th>
      <th class="sun">日</th>
    </tr>
  </thead>
  <tbody>
    {#each weeks as week}
      <tr>
        {#each week as day, i}
          {#if i % 7 === 5}
            <td class="sat">{day}</td>
          {:else if i % 7 === 6}
            <td class="sun">{day}</td>
          {:else}
            <td>{day}</td>
          {/if}
        {/each}
      </tr>
    {/each}
  </tbody>
</table>
