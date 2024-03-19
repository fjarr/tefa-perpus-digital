<template>
  <div>
    <canvas id="myChart"></canvas>
  </div>
</template>

<script setup lang="ts">
import Chart, { type ChartConfiguration, type ChartItem } from 'chart.js/auto';

const labels = [
  'January',
  'February',
  'March',
  'April',
  'May',
  'June',
  'july',
  'august',
  'september',
  'October',
  'November',
  'December'
];

const data = {
  labels: labels,
  datasets: [{
    label: 'Pengunjung',
    backgroundColor: ' #5b89ff',
    data: [2, 5, 5, 10, 5, 8, 10, 4.3, 2, 2, 5, 2],
  }]
};

const config: ChartConfiguration = {
  type: 'bar',
  data: data,
  options: {}
};

onMounted(() => {
  const canvasTag = <ChartItem>document.getElementById('myChart')
  new Chart(
    canvasTag,
    config
  );
})
</script>

<style scoped>
#myChart {
  width: 900px;
}


@media only screen and (max-width: 820px) {
  #myChart {
    width: 320px;
  }
}
</style>