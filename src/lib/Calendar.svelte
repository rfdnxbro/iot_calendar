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
      for (let j = 0; j < 7; j++) {
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
  th {
    background-color: #f2f2f2;
  }
  button {
    cursor: pointer;
  }
</style>

<div>
  <button on:click={prevMonth}>&lt; 前の月</button>
  <span>{currentYear}年 {currentMonth + 1}月</span>
  <button on:click={nextMonth}>次の月 &gt;</button>
</div>

<table>
  <thead>
    <tr>
      <th>日</th>
      <th>月</th>
      <th>火</th>
      <th>水</th>
      <th>木</th>
      <th>金</th>
      <th>土</th>
    </tr>
  </thead>
  <tbody>
    {#each weeks as week}
      <tr>
        {#each week as day}
          <td>{day}</td>
        {/each}
      </tr>
    {/each}
  </tbody>
</table>
