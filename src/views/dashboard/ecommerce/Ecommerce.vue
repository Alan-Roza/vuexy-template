<template>
  <container class="container-scroll">
    <section
      id="home"
      class="section-image"
    >
      <div class="position-relative">
        <img
          src="@/assets/images/upx/roof-hd.jpg"
          alt="telhado verde"
          class="green-roof"
        >
        <div class="roof-text">
          <img
            class="roof-text"
            src="@/assets/images/upx/text.png"
            alt="texto"
          >
        </div>
      </div>
    </section>

    <section
      id="about"
      class="section-about"
    >
      <div class="dashboard-text">
        O que é Telhado Verde?
      </div>
      <div style="font-size: 17px; margin-bottom: 30px">
        Telhado verde é uma cobertura de plantas e um telhado ecológico que tem ganhado cada vez mais espaço nas construções.
        Composto por vegetação, ele é mais que uma cobertura verde e envolve técnicas deimpermeabilização e de plantio que devem ser feitas por um profissional qualificado.
        A partir do telhado verde é possível ter um aproveitamento melhor da luz do sol, bem como mais frescor para dentro de casa.
      </div>

      <div class="dashboard-text">
        Benefícios do Telhado Verde
      </div>
      <div style="font-size: 17px">
        <ul>
          <li>
            Diminui a poluição e melhora a qualidade do ar das cidades. A vegetação absorve as substâncias tóxicas e a libera oxigênio na atmosfera.
          </li>
          <li>
            Ajuda a combater o efeito de Ilhas de Calor nas grandes cidades.
          </li>
          <li>
            Melhora o isolamento térmico da edificação. Protege contra as altas temperatura no verão e ajuda a manter a temperatura interna no inverno
          </li>
          <li>
            Melhora o isolamento acústico da edificação. A vegetação absorve e isola ruídos.
          </li>
          <li>
            Maior retenção da água das chuvas. A vegetação auxilia na drenagem da água da chuva, reduzindo assim a necessidade de escoamento de água e de sistemas de esgoto e ainda filtra a poluição dessas águas.
          </li>
          <li>
            Diminui a possibilidade de enchentes. Como retem melhor a água da chuva, o excesso não vai para as ruas.
          </li>
          <li>
            Ajuda na diminuição da temperatura do micro e macro ambientes externo.
          </li>
          <li>
            Reduz o consumo de energia, e melhora a eficiência energética devido à redução da temperatura no ambiente interno, diminuindo a necessidade de refrigeração.
          </li>
          <li>
            Aumento da biodiversidade, a criação do telhado verde também é a criação de um habitat, portanto atrai pássaros, borboletas entre outros.
          </li>
          <li>
            Valorização do Imóvel: Os imóveis que recebem o projeto tendem a ser mais valorizados no mercado, devido aos benefícios que ele traz.
          </li>
        </ul>
      </div></section>

    <section id="dashboard">
      <div class="dashboard-text">
        Dashboard
      </div>
      <b-row class="match-height">
        <b-col
          lg="6"
          md="12"
        >
          <analytics-congratulation :data="data.congratulations" />
        </b-col>
        <b-col
          lg="3"
          sm="6"
        >
          <statistic-card-with-area-chart
            v-if="externa.temperature"
            icon="SunIcon"
            color="danger"
            :statistic="
              kFormatter(externa.temperature.analyticsData.current)
            "
            statistic-title="Temperatura Externa"
            :chart-data="temp"
          />

        </b-col>
        <b-col
          lg="3"
          sm="6"
        >
          <statistic-card-with-area-chart
            v-if="interna.temperature"
            icon="SunIcon"
            color="warning"
            :statistic="
              kFormatter(interna.temperature.analyticsData.current)
            "
            statistic-title="Temperatura Interna"
            :chart-data="interna.temperature.series"
          />
        </b-col>
      </b-row>

      <b-row class="match-height">
        <b-col lg="12">
          <b-row class="match-height">
            <b-col
              lg="4"
              md="6"
            >
              <!-- {{ humidade }} -->
              <ecommerce-goal-overview :data="data.goalOverview" />
            </b-col>
            <b-col lg="4">
              <analytics-timeline :data="timeline" />
            </b-col>
            <b-col lg="4">
              <analytics-support-tracker :data="data.suporteTrack" />
            </b-col>
          </b-row>
        </b-col>

      </b-row>
    </section>
  </container>
</template>

<script>
import { BRow, BCol } from 'bootstrap-vue'

// import { getUserData } from '@/auth/utils'
import StatisticCardWithAreaChart from '@core/components/statistics-cards/StatisticCardWithAreaChart.vue'
import { kFormatter } from '@core/utils/filter'
import AnalyticsSupportTracker from './AnalyticsSupportTracker.vue'
import AnalyticsTimeline from './AnalyticsTimeline.vue'
import AnalyticsCongratulation from './AnalyticsCongratulation.vue'
// import EcommerceRevenueReport from './EcommerceRevenueReport.vue'
// import EcommerceOrderChart from './EcommerceOrderChart.vue'
// import EcommerceProfitChart from './EcommerceProfitChart.vue'
// import EcommerceEarningsChart from './EcommerceEarningsChart.vue'
// import EcommerceCompanyTable from './EcommerceCompanyTable.vue'
// import EcommerceMeetup from './EcommerceMeetup.vue'
// import EcommerceBrowserStates from './EcommerceBrowserStates.vue'
import EcommerceGoalOverview from './EcommerceGoalOverview.vue'

export default {
  components: {
    BRow,
    BCol,
    StatisticCardWithAreaChart,
    AnalyticsCongratulation,
    AnalyticsTimeline,
    AnalyticsSupportTracker,
    // EcommerceRevenueReport,
    // EcommerceOrderChart,
    // EcommerceProfitChart,
    // EcommerceEarningsChart,
    // EcommerceCompanyTable,
    // EcommerceMeetup,
    // EcommerceBrowserStates,
    EcommerceGoalOverview,
  },
  data() {
    return {
      data: {
        goalOverview: {
          // completed: '786,617',
          // inProgress: '13,561',
          series: [
            83,
          ],
        },
        congratulations: {
          name: 'Alan',
          saleToday: '0',
        },
        suporteTrack: {
          lastDays: ['last 28', 'last month'],
          supportTrackerRadialBar: {
            series: [100],
          },
          newTicket: 29,
          openTicket: 20,
          responseTime: 1,
          title: 'luz',
          totalTicket: 160,
        },
      },

      timeline: {
        step1: {
          // duration: '12 min',
          subtitle: 'Está em 83%',
          title: 'Humidade do solo',
        },
        step2: {
          // duration: '12 min',
          subtitle: 'Está em 23℃',
          title: 'Temperatura externa',
        },
        step3: {
          // duration: '12 min',
          subtitle: 'Está em 100%',
          title: 'Sistema de iluminação',
        },
        step4: {
          // duration: '12 min',
          subtitle: 'Está em 23℃',
          title: 'Temperatura interna',
        },
        step5: {
          // duration: '12 min',
          subtitle: 'Está ligado',
          title: 'Irrigação automática',
        },
      },
      fullData: {},

      // temperatura
      externa: {
        temperature: {
          series: [
            {
              name: 'Temperatura',
              data: [32, 28, 22, 23],
            },
          ],
          analyticsData: {
            current: '23',
          },
        },
      },
      interna: {
        temperature: {
          series: [
            {
              name: 'Temperatura',
              data: [30, 27, 21, 23],
            },
          ],
          analyticsData: {
            current: '23',
          },
        },
      },
    }
  },

  computed: {
    temp() {
      return this.externa.temperature.series
    },
    tempInt() {
      return this.interna.temperature.series
    },
  },

  watch: {
    scroll() {
      window.addEventListener('hashchange', () => window.scrollTo(window.scrollX, window.scrollY - 100))
    },
  },

  created() {
    setInterval(() => {
      fetch('https://api.thingspeak.com/channels/1556327/feeds.json?results=1')
        .then(response => response.json())
        .then(data => {
          //         this.fullData = data
          // this.data.goalOverview.series.push(data.feeds[0].field3)
          // this.interna.temperature.AnalyticsTimeline.current = data.feeds[0].field2
          data.feeds.forEach(result => {
            if (result.field1 !== null) {
              this.externa.temperature.analyticsData.current = result.field1
              this.timeline.step2.subtitle = `Está em ${result.field1}℃`
              if (this.externa.temperature.series[0].data[(this.externa.temperature.series[0].data.length - 1)] !== parseFloat(result.field1)) {
                this.externa.temperature.series[0].data.push(parseFloat(result.field1))
              }
            }
            if (result.field2 !== null) {
              this.interna.temperature.analyticsData.current = result.field2
              this.timeline.step4.subtitle = `Está em ${result.field2}℃`
              if (this.interna.temperature.series[0].data[(this.interna.temperature.series[0].data.length - 1)] !== parseFloat(result.field2)) {
                this.interna.temperature.series[0].data.push(parseFloat(result.field2))
              }
            }
            if (result.field1 - result.field2 >= 0) {
              this.data.congratulations.saleToday = result.field1 - result.field2
            } else this.data.congratulations.saleToday = 0
            if (result.field3 && this.data.goalOverview.series[0] !== parseFloat(result.field3)) {
              this.data.goalOverview.series = [parseFloat(result.field3 > 100 ? 100 : result.field3)]
              this.timeline.step1.subtitle = `Está em ${result.field3 > 100 ? 100 : result.field3}%`
            }
            if (result.field4) {
              this.timeline.step3.subtitle = `Está em ${result.field4}%`
              console.log(result.field4)
              this.data.suporteTrack.supportTrackerRadialBar.series = [parseFloat(result.field4)]
            }
            if (result.field5) {
              this.timeline.step5.subtitle = `Está ${parseFloat(result.field5) === 0 ? 'desligado' : 'ligado'}`
            }
          })
        })
    }, 10000)

    // data
    // this.$http.get('/ecommerce/data').then(response => {
    // this.data = response.data
    // console.log(response.data)

    // ? Your API will return name of logged in user or you might just directly get name of logged in user
    // ? This is just for demo purpose
    // const userData = getUserData()
    // this.data.congratulations.name = userData.fullName.split(' ')[0] || userData.username
    // })

    // this.$http.get('https://api.thingspeak.com/channels/1552907/feeds.json?api_key=HM30N5H1K70GRR25&results=1').then(response => {
    // })
  },
  methods: {
    kFormatter,
  },
}
</script>

<style lang="scss">
@import "@core/scss/vue/pages/dashboard-ecommerce.scss";
@import "@core/scss/vue/libs/chart-apex.scss";
#home {
  padding-top: 150px;
  margin-top: -150px;
}
#dashboard {
  padding-top: 150px;
  margin-top: -150px;
}
#about {
  padding-top: 150px;
  margin-top: -150px;
}
::-webkit-scrollbar {
  width: 8px;
  width: 11px;
}
::-webkit-scrollbar-track {
  background: #ffffff;
}
::-webkit-scrollbar-thumb {
  background: #ffa228;
  border-radius: 20px;
  border: 0.2em solid #ffffff;
}
::-webkit-scrollbar-thumb:hover {
  background: #ffa228;
}

.section-image {
  margin-bottom: 50px;
}

.section-about {
  padding-bottom: 50px;
  max-width: calc(100% - 300px);
  margin: auto;
  @media (max-width: 1200px) {
    max-width: 100%
  }
}

.dashboard-text {
  font-size: 35px;
}

html {
  scroll-behavior: smooth;
}

.green-roof {
  background-attachment: fixed;
  background-position: center;
  width: calc(100% + 65px);
  margin-left: -30px;
  margin-top: -250px;
  @media (max-width: 1200px) {
    margin-top: -120px;
    width: calc(100% + 120px);
  }
  @media (max-width: 768px) {
    height: auto;
    width: auto;
    margin-top: -130px;
  }
  @media (max-width: 545px) {
    transform: translate(-20%);
  }
}

.position-relative {
  position: relative;
  justify-content: center;
  text-align: center;
  margin-bottom: -350px;
    @media (max-width: 991px) {
    display: none;
  }
}

.roof-text {
  margin-left: auto;
  margin-right: auto;
  transform: translate(0, -90%);
  height: 200px;
}
</style>
