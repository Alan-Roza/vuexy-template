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
            v-if="hardCodedData.temperature"
            icon="SunIcon"
            color="danger"
            :statistic="
              kFormatter(hardCodedData.temperature.analyticsData.current)
            "
            statistic-title="Temperatura Externa"
            :chart-data="hardCodedData.temperature.series"
          />
        </b-col>
        <b-col
          lg="3"
          sm="6"
        >
          <statistic-card-with-area-chart
            v-if="hardCodedData.temperature"
            icon="SunIcon"
            color="warning"
            :statistic="
              kFormatter(hardCodedData.temperature.analyticsData.current)
            "
            statistic-title="Temperatura Interna"
            :chart-data="hardCodedData.temperature.series"
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
              <ecommerce-goal-overview :data="data.goalOverview" />
            </b-col>
            <b-col lg="4">
              <analytics-timeline :data="timeline" />
            </b-col>
            <b-col lg="4">
              <analytics-support-tracker :data="suporteTrack" />
            </b-col>
          </b-row>
        </b-col>
      </b-row>
    </section>
  </container>
</template>

<script>
import { BRow, BCol } from 'bootstrap-vue'

import { getUserData } from '@/auth/utils'
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
      data: {},
      timeline: {
        step1: {
          duration: '12 min',
          fileName: 'data.json',
          img: 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACEAAAAkCAMAAAAw96PuAAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAIaADAAQAAAABAAAAJAAAAADeoA9wAAABcVBMVEUAAAD/qlX/qlX/n2D/qlX/n1D/pUv/qkf/oUP/pk3/qkn/okb/o0f/okT/n0j/oEn/n0b/pEn/oEf/okb/oUj/o0f/n0X/oUT/o0f/oEb/pEP/okb/n0T/okT/oEb/n0T/oEX/o0b/n0P/oUP/okb/oUT/n0b/oUX/oET/oUb/n0X/oET/oUP/oEX/okT/oEP/oUX/oUP/oET/oUX/oEX/n0T/oEX/oET/oEX/n0T/oET/n0P/oEX/n0P/oUT/n0T/oEX/oUT/oET/oEP/oET/oUT/oEP/oEP/oET/oEP/oEP/oET/n0T/oET/oEP/n0T/oET/n0T/n0T/oET/n0T/n0P/oET/n0P/oET/n0T/oEP/oET/oET/n0T/n0T/oEP/oEP/n0P/oET/n0P/n0T/n0T/n0P/oEP/n0T/oEP/n0P/oET/n0T/oEP/oET/n0T/oET/oEP/n0T/oEP/oET/n0P/oEP/oET/n0T/oEP/n0NWaDR5AAAAenRSTlMAAwYICRAREhMUFRYZHiAjKCorLC4vMDEyMzU3ODw+QENFSExNT1BRU1RVVldZWltcX2Zna21zdHZ4e31+hYeIkZKTlJmam5yen6OkpaanqKmtsLG4ury9v8DBw8fIytHU1dfY2t3g5OXn6Onq6+zt7u/w8/n6+/z9/jLTlDYAAAE3SURBVDjL7dRHUwIxFMDxZ0OsIAoqtijqYhcVCxZQZO0iWLAXYC0IsqIivE/vRh2GLLs5evJ/yLyZ/CaHzCQAAAbxAZmezMBUfoPqEk2McGFpz5Zi4VPtyjllSTYXiYBKRCYpSbVwBIx/UmLlCBij5MXGETCaVYZ0G0fAMCVyO0eA80MZX+0cAQIlmVaOgAFK5rREbOq3sJ5g+hcaQvweTyOYCPjjiMf+c2XZyeP+PSsER6rW2ruNQzWDlW4ksIlVB2pxBnuIR3CCqxAjlvo3Y4nITgCRlsve8RZCxGP2NgRZ0S8gXpuc6xDFEFyRhWBdI3NGdM2wKC1tmEbSxr5dmz1H5vMdwIhw13TmTuh2JzHu6pmV0bOFl46Lv71TH0/M6P0OhTp1fphChz8Po1p81N6XVioAvgBZgp3AxW+3KgAAAABJRU5ErkJggg==',
          subtitle: 'subtitle',
          title: 'title',
        },
        step2: {
          avatar: '/img/avatar-s-9.397f0acd.jpg',
          avatarName: 'John',
          occupation: 'CEO',
          duration: '12 min',
          subtitle: 'subtitle',
          title: 'title',
        },
        step3: {
          avatar: '/img/avatar-s-9.397f0acd.jpg',
          avatarName: 'John',
          occupation: 'CEO',
          duration: '12 min',
          subtitle: 'subtitle',
          title: 'title',
        },
        step4: {
          avatar: '/img/avatar-s-9.397f0acd.jpg',
          avatarName: 'John',
          occupation: 'CEO',
          duration: '12 min',
          subtitle: 'subtitle',
          title: 'title',
        },
      },
      suporteTrack: {
        lastDays: ['last 28', 'last month'],
        supportTrackerRadialBar: {
          series: [83],
        },
        newTicket: 29,
        openTicket: 20,
        responseTime: 1,
        title: 'luz',
        totalTicket: 160,
      },
      hardCodedData: {
        temperature: {
          series: [
            {
              name: 'Temperatura',
              data: [24, 23, 22, 24, 25, 27],
            },
          ],
          analyticsData: {
            current: '27℃',
          },
        },
      },
    }
  },
  watch: {
    scroll() {
      console.log('foi')
      window.addEventListener('hashchange', () => window.scrollTo(window.scrollX, window.scrollY - 100))
    },
  },
  created() {
    // data
    this.$http.get('/ecommerce/data').then(response => {
      this.data = response.data

      // ? Your API will return name of logged in user or you might just directly get name of logged in user
      // ? This is just for demo purpose
      const userData = getUserData()
      this.data.congratulations.name = userData.fullName.split(' ')[0] || userData.username
    })

    this.$http.get('https://api.thingspeak.com/channels/1552907/feeds.json?api_key=HM30N5H1K70GRR25&results=1').then(response => {
      console.log(response, 'response')
    })
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
