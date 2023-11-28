<script>
import Button from './Button.vue'
export default {
  components: {
    Button,
  },
}
</script>
<template>
  <header class="header">
    <div class="header__logo">
      <img class="header__logo-img" src="/assets/svg/logo.svg" alt="logo" />
      <h1 class="header__logo-title">brix <span>templates</span></h1>
    </div>

    <Button label="Clone now" />
  </header>
</template>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  padding: 42px 0 45px 0;
  &__logo {
    display: flex;
    align-items: center;
    gap: 16px;
    &-img {
      width: 40px;
      height: 40px;
    }
    &-title {
      font-size: 36px;
      color: #170f49;
      font-weight: 900;
      & span {
        color: #4a3aff;
      }
    }
  }
}
</style>
