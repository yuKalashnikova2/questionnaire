<script>
export default {}
</script>
<template>
  <header class="header">
    <div class="header__logo">
      <img class="header__logo-img" src="/assets/svg/logo.svg" alt="logo" />
      <h1 class="header__logo-title">brix <span>templates</span></h1>
    </div>

    <button class="button">Clone now</button>
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
.button {
  padding: 20px 40px;
  border-radius: 56px;
  background: #4a3aff;
  border: none;
  color: #fff;
  text-align: center;

  font-size: 18px;
  font-weight: 700;
  line-height: 20px;
}
</style>
