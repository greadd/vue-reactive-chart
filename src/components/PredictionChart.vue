<template>
  <div class="wrapper">
    <span class="chart-title">Подписчики</span>
    <line-chart
      :chart-data="dataCollection"
      :options="options"
      :width="661"
      :height="209"
      @setGradient="setBgColor"
    ></line-chart>
  </div>
</template>

<script>
import LineChart from '@/components/LineChart'
export default {
  name: 'PredictionChart',
  components: {
    LineChart
  },
  props: {
    budget: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      gradient: {},
      dataCollection: {},
      options: {
        maintainAspectRatio: false,
        responsive: true,
        legend: {
          display: false
        },
        tooltips: {
          enabled: false
        },
        scales: {
          yAxes: [
            {
              ticks: {
                min: 0,
                display: true,
                maxTicksLimit: 6,
                fontColor: 'rgba(33, 33, 33, 1)',
                fontFamily: "'PT Sans', sans-serif",
                fontSize: 13,
                lineHeight: '18px',
                padding: 20
              },
              gridLines: {
                display: true,
                zeroLineWidth: 2,
                zeroLineColor: '#E2E5EE',
                color: 'rgba(0,0,0,0)'
              }
            }
          ],
          xAxes: [
            {
              gridLines: {
                display: true,
                zeroLineWidth: 2,
                zeroLineColor: '#E2E5EE',
                borderDash: [5],
                color: '#E2E5EE'
              },
              ticks: {
                fontColor: 'rgba(33, 33, 33, 1)',
                display: true,
                fontFamily: "'PT Sans', sans-serif",
                fontSize: 13,
                lineHeight: '18px',
                padding: 13
              }
            }
          ]
        }
      }
    }
  },
  watch: {
    budget() {
      this.update()
    }
  },
  mounted() {
    if (window.screen.width < 540) {
      this.options.scales.yAxes[0].ticks.padding = 8
      this.options.scales.xAxes[0].ticks.padding = 8
    }
    window.addEventListener('resize', this.resizeChart)
    this.update()
  },
  destroyed() {
    window.removeEventListener('resize', this.resizeChart)
  },
  methods: {
    resizeChart(e) {
      const x = this.options.scales.xAxes[0]
      const y = this.options.scales.yAxes[0]
      if (e.target.innerWidth < 540) {
        y.ticks.padding = 8
        y.ticks.fontSize = 12
        x.ticks.padding = 8
        x.ticks.fontSize = 12
        x.ticks.lineHeight = '16px'
        y.ticks.lineHeight = '16px'
      } else {
        y.ticks.padding = 20
        y.ticks.fontSize = 13
        x.ticks.padding = 13
        x.ticks.fontSize = 13
        x.ticks.lineHeight = '18px'
        y.ticks.lineHeight = '18px'
      }
      this.update()
    },
    update() {
      this.dataCollection = {
        labels: [
          '1 день',
          '2 день',
          '3 день',
          '4 день',
          '5 день',
          '6 день',
          '7 день'
        ],
        datasets: [
          {
            backgroundColor: this.gradient,
            data: this.fillData(),
            pointRadius: 3.5,
            pointBorderWidth: 2,
            pointBackgroundColor: '#ffffff',
            pointHoverRadius: 3.5,
            pointHoverBorderWidth: 2,
            pointHoverBorderColor: '#7045C4',
            pointHoverBackgroundColor: '#7045C4',
            borderWidth: 2,
            borderColor: '#7045C4'
          }
        ]
      }
    },
    fillData() {
      const data = [0]
      for (let i = 1; i < 7; i++) {
        data.push(data[i - 1] + (this.budget / 4 / 30) * Math.random())
      }
      return data
    },
    setBgColor(gradient) {
      this.gradient = gradient
    }
  }
}
</script>

<style scoped lang="scss">
.wrapper {
  border: 1px solid #e2e5ee;
  border-radius: 6px;
  padding: 37px 20px;
  margin-left: 30px;
}
.chart-title {
  display: none;
  font-family: 'PT Sans', sans-serif;
  color: #212121;
  font-size: 15px;
  line-height: 18px;
  margin-left: 5px;
  margin-bottom: 16px;
}
@media (max-width: 960px) {
  .wrapper {
    margin-left: 0;
    padding: 37px 50px;
  }
}
@media (max-width: 540px) {
  .wrapper {
    padding: 15px 15px;
  }
}
@media (max-width: 414px) {
  .wrapper {
    border-radius: 0;
  }
  .chart-title {
    display: block;
  }
}
</style>
