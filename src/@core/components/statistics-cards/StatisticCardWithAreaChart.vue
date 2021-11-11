<template>
  <b-card no-body>
    <b-card-body class="pb-0">
      <b-avatar
        class="mb-1"
        :variant="`light-${color}`"
        size="45"
      >
        <feather-icon
          size="21"
          :icon="icon"
        />
      </b-avatar>
      <div class="truncate">
        <h2 class="mb-25 font-weight-bolder">
          {{ statistic }}℃
        </h2>
        <span>{{ statisticTitle }}</span>
      </div>
    </b-card-body>

    <vue-apex-charts
      ref="realtimeChart"
      type="area"
      height="100"
      width="100%"
      :options="chartOptionsComputed"
      :series="tempt"
    />

  </b-card>
</template>

<script>
import { BCard, BCardBody, BAvatar } from 'bootstrap-vue'
import VueApexCharts from 'vue-apexcharts'
import { $themeColors } from '@themeConfig'
import { areaChartOptions } from './chartOptions'

export default {
  components: {
    VueApexCharts,
    BCard,
    BCardBody,
    BAvatar,
  },
  props: {
    icon: {
      type: String,
      required: true,
    },
    statistic: {
      type: [Number, String],
      required: true,
    },
    statisticTitle: {
      type: String,
      default: '',
    },
    color: {
      type: String,
      default: 'primary',
    },
    chartData: {
      type: Array,
      default: () => [],
    },
    chartOptions: {
      type: Object,
      default: null,
    },
  },

  data() {
    return {
      tempt: this.chartData,
    }
  },
  computed: {
    temp() {
      console.log(this.chartData, 'chart')
      return this.chartData
    },
    chartOptionsComputed() {
      if (this.chartOptions === null) {
        const options = JSON.parse(JSON.stringify(areaChartOptions))
        options.theme.monochrome.color = $themeColors[this.color]
        return options
      }
      return this.chartOptions
    },
  },
  beforeUpdate() {
    this.updateSeries()
  },
  methods: {
    updateSeries() {
      window.dispatchEvent(new Event('resize'))
    },
    updateSeriesLine() {
      this.$refs.realtimeChart.updateSeries([{
        data: this.chartData,
      }], true)
    },
  },
}
</script>
