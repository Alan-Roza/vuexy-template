<template>
  <p class="clearfix mb-0">
    <span class="float-md-left d-block d-md-inline-block mt-25">
      COPYRIGHT  © {{ new Date().getFullYear() }}
      <b-link
        class="ml-25"
        href="https://github.com/RozaAlan/UPx4-Dashboard"
        target="_blank"
      >Github</b-link>
      <span class="d-none d-sm-inline-block">, Todos os Direitos Reservados</span>
    </span>

    <span class="float-md-right d-none d-md-block">Projeto de UPx 4 - Facens
      <feather-icon
        icon="LayersIcon"
        size="21"
        class="text-danger stroke-current"
      />
    </span>
  </p>
</template>

<script>
import { BLink } from 'bootstrap-vue'

export default {
  components: {
    BLink,
  },
}
</script>
