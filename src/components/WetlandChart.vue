<template>
  <div class="wetland-chart-container" ref="container"></div>
</template>

<script setup lang="ts">
import useEcharts from '@/hooks/useEcharts'

const { container, setOption } = useEcharts()

const generateWetlandChartOptions = () => {
  return {
    legend: {
      show: true,
      right: 0,
      textStyle: {
        color: '#fff',
      },
    },
    tooltip: {
      trigger: 'axis',
      backgroundColor: '#000',
      borderColor: '#333',
      textStyle: {
        color: '#fff',
      },
    },
    grid: {
      left: '4%',
      right: '4%',
      bottom: '0%',
      top: '20%',
      containLabel: true,
    },
    xAxis: {
      type: 'category',
      axisLine: {
        show: false,
      },
      axisTick: {
        show: false,
      },
      axisLabel: {
        color: '#fff',
        margin: 10,
      },
      data: ['湿地A', '湿地B', '湿地C', '湿地D', '湿地E'],
    },
    yAxis: {
      type: 'value',
      axisLabel: {
        color: '#fff',
      },
      splitLine: {
        lineStyle: {
          color: '#c8c8c830',
          type: 'dashed',
        },
      },
    },
    series: [
      {
        name: '湿地水位',
        type: 'line',
        data: [320, 332, 301, 334, 390],
        itemStyle: {
          color: 'rgba(87, 153, 214, 1)',
        },
      },
      {
        name: '湿地污染指数',
        type: 'bar',
        data: [220, 182, 191, 234, 290],
        itemStyle: {
          color: 'rgba(0, 254, 169, 1)',
        },
      },
    ],
  }
}

const options = generateWetlandChartOptions()
setOption(options)

return {
  container
}
</script>

<style scoped lang="scss">
.wetland-chart-container {
  width: 100%;
  height: 400px; /* 可以根据需要调整图表的高度 */
}
</style>
