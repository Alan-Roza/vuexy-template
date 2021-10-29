<template>
  <div>
    <div class="navbar-container main-menu-content">
      <a
        class="button-nav"
        href="#home"
      >
        Casa
      </a>
    </div>
    <div class="navbar-container main-menu-content">
      <a
        class="button-nav-home"
        href="#about"
      >
        Sobre
      </a>
    </div>
    <div class="navbar-container main-menu-content">
      <a
        class="button-nav-question"
        href="#dashboard"
      >
        Dashboard
      </a>
    </div>

  </div>
</template>

<script>
import navMenuItems from '@/navigation/horizontal'

export default {
  components: {
  },
  setup() {
    return {
      navMenuItems,
    }
  },
}
</script>

<style lang="scss">
@import "~@core/scss/base/core/menu/menu-types/horizontal-menu.scss";

.button-nav {
  transition: 250ms;
  position: absolute;
  margin-top: 13px;
  color: white;
  border-radius: 4px;
  font-weight: bold;
  padding: 11px 40px;
  background-image: linear-gradient(#ffc170, #FFA228);
  &:hover {
    color: rgb(255, 247, 235);
    background-image: linear-gradient(#f8b864, #fca22e);
  }
}
.button-nav-home {
  transition: 250ms;
  transform: translate(120%);
  position: absolute;
  margin-top: 13px;
  color: white;
  border-radius: 4px;
  font-weight: bold;
  padding: 11px 40px;
  background-image: linear-gradient(#ffc170, #FFA228);
  &:hover {
    color: rgb(255, 247, 235);
    background-image: linear-gradient(#f8b864, #fca22e);
  }
}
.button-nav-question {
  transition: 250ms;
  transform: translate(190%);
  position: absolute;
  margin-top: 13px;
  color: white;
  border-radius: 4px;
  font-weight: bold;
  padding: 11px 40px;
  background-image: linear-gradient(#ffc170, #FFA228);
  &:hover {
    color: rgb(255, 247, 235);
    background-image: linear-gradient(#f8b864, #fca22e);
  }
}

</style>
