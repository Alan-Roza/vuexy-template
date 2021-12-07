<template>
  <b-card
    v-if="data"
    text-variant="center"
    class="card card-congratulations"
  >
    <!-- images -->
    <b-img
      :src="require('@/assets/images/elements/decore-left.png')"
      class="congratulations-img-left"
    />
    <b-img
      :src="require('@/assets/images/elements/decore-right.png')"
      class="congratulations-img-right"
    />
    <!--/ images -->

    <b-avatar
      variant="primary"
      size="70"
      class="shadow mb-2"
    >
      <feather-icon
        size="28"
        icon="AwardIcon"
      />
    </b-avatar>
    <h1
      v-if="data.saleToday > 0"
      class="mb-1 mt-50 text-white"
    >
      Isso é incrível!
    </h1>
    <h1
      v-else
      class="mb-1 mt-50 text-white"
    >
      Continue de olho!
    </h1>
    <b-card-text
      v-if="data.saleToday > 0"
      class="m-auto w-75"
    >
      Você conseguiu uma redução de temperatura em relação ao ambiente externo.
    </b-card-text>
    <b-card-text
      v-else
      class="m-auto w-75"
    >
      Você não conseguiu ainda uma redução de temperatura em relação ao ambiente externo.
    </b-card-text>
  </b-card>
</template>

<script>
import {
  BCard, BImg, BAvatar, BCardText,
} from 'bootstrap-vue'

export default {
  components: {
    BCard,
    BAvatar,
    BImg,
    BCardText,
  },
  props: {
    data: {
      type: Object,
      default: () => {},
    },
  },
}
</script>
