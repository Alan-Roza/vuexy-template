<template>
  <div
    class="navbar-container d-flex content align-items-center"
    style="height: 70px"
  >

    <!-- Nav Menu Toggler -->
    <ul class="nav navbar-nav d-xl-none">
      <li class="nav-item">
        <b-link
          class="nav-link"
          @click="toggleVerticalMenuActive"
        >
          <feather-icon
            icon="MenuIcon"
            size="21"
          />
        </b-link>
      </li>
    </ul>

    <!-- Left Col -->
    <!-- <div class="bookmark-wrapper align-items-center flex-grow-1 d-none d-lg-flex">
      <bookmarks />
    </div> -->

    <!-- Right Col -->
    <b-navbar-nav class="nav align-items-center ml-auto">
      <locale />
      <dark-Toggler class="d-none d-lg-block" />
      <notification-dropdown />
    </b-navbar-nav>
  </div>
</template>

<script>
import {
  BLink, BNavbarNav,
} from 'bootstrap-vue'
// import Bookmarks from './components/Bookmarks.vue'
import Locale from './components/Locale.vue'
import DarkToggler from './components/DarkToggler.vue'
import NotificationDropdown from './components/NotificationDropdown.vue'

export default {
  components: {
    BLink,

    // Navbar Components
    BNavbarNav,
    // Bookmarks,
    Locale,
    DarkToggler,
    NotificationDropdown,
  },
  props: {
    toggleVerticalMenuActive: {
      type: Function,
      default: () => {},
    },
  },

}
</script>
