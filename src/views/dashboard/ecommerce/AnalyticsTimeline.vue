<template>
  <b-card
    v-if="data"
    no-body
  >
    <b-card-header>
      <b-card-title class="ml-25">
        ÚLTIMAS MUDANÇAS
      </b-card-title>
    </b-card-header>

    <!-- timeline -->
    <b-card-body>
      <app-timeline>
        <app-timeline-item variant="primary">
          <div class="d-flex justify-content-between flex-sm-row flex-column mb-sm-0 mb-2">
            <h6>{{ data.step1.title }}</h6>
            <small class="timeline-item-time text-nowrap text-muted ml-1">{{ data.step1.duration }}</small>
          </div>
          <p>{{ data.step1.subtitle }}</p>
        </app-timeline-item>

        <app-timeline-item variant="warning">
          <div class="d-flex justify-content-between flex-sm-row flex-column mb-sm-0 mb-2">
            <h6>{{ data.step2.title }}</h6>
            <small class="timeline-item-time text-nowrap text-muted ml-1">{{ data.step2.duration }}</small>
          </div>
          <p>{{ data.step2.subtitle }}</p>
        </app-timeline-item>

        <app-timeline-item variant="info">
          <div class="d-flex justify-content-between flex-sm-row flex-column mb-sm-0 mb-2">
            <h6>{{ data.step3.title }}</h6>
            <small class="timeline-item-time text-nowrap text-muted ml-1">{{ data.step3.duration }}</small>
          </div>
          <p>{{ data.step3.subtitle }}</p>
        </app-timeline-item>

        <app-timeline-item variant="success">
          <div class="d-flex justify-content-between flex-sm-row flex-column mb-sm-0 mb-2">
            <h6>{{ data.step3.title }}</h6>
            <small class="timeline-item-time text-nowrap text-muted ml-1">{{ data.step3.duration }}</small>
          </div>
          <p>{{ data.step3.subtitle }}</p>
        </app-timeline-item>

        <app-timeline-item
          :title="data.step4.title"
          :subtitle="data.step4.subtitle"
          :time="data.step4.duration"
          variant="danger"
        />
      </app-timeline>
      <!--/ timeline -->
    </b-card-body>
  </b-card>
</template>

<script>
import {
  BCard, BCardBody, BCardHeader, BCardTitle, VBTooltip,
} from 'bootstrap-vue'
import AppTimeline from '@core/components/app-timeline/AppTimeline.vue'
import AppTimelineItem from '@core/components/app-timeline/AppTimelineItem.vue'
/* eslint-disable global-require */
export default {
  components: {
    BCard,
    BCardBody,
    BCardHeader,
    BCardTitle,
    AppTimeline,
    AppTimelineItem,
  },
  directives: {
    'b-tooltip': VBTooltip,
  },
  props: {
    data: {
      type: Object,
      default: () => {},
    },
  },
}
</script>
