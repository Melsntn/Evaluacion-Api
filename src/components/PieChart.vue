<!-- PieChart.vue -->
<template>
    <div>
      <canvas ref="pieChart"></canvas>
    </div>
  </template>
  
  <script>
  import { Pie } from 'vue-chartjs';
  
  export default {
    extends: Pie,
    props: ['data', 'labels'],
    mounted() {
      this.renderChart({
        labels: this.labels,
        datasets: [
          {
            backgroundColor: ['#FF6384', '#36A2EB'],
            data: this.data,
          },
        ],
      }, { responsive: true, maintainAspectRatio: false });
    },
  };
  </script>
  
  <style scoped>
  /* Puedes agregar estilos personalizados para la gráfica aquí */
  </style>
  