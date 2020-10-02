<script>
import { Line, mixins } from 'vue-chartjs'
const { reactiveProp } = mixins

export default {
  extends: Line,
  mixins: [reactiveProp],
  props: {
    chartData: {
      type: Object,
      default() {
        return {}
      }
    },
    options: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  watch: {
    chartData() {
      this.getGradient()
      this.renderChart(this.chartData, this.options)
    }
  },
  mounted() {
    this.getGradient()
    this.renderChart(this.chartData, this.options)
  },
  methods: {
    getGradient() {
      const gradient = this.$refs.canvas
        .getContext('2d')
        .createLinearGradient(0, 90, 0, 220)
      gradient.addColorStop(0, 'rgba(142, 86, 233, 0.31)')
      gradient.addColorStop(0.87, 'rgba(142, 86, 233, 0)')
      this.$emit('setGradient', gradient)
    }
  }
}
</script>
