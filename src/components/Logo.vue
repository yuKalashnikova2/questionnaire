<script>
export default {
    props: {
        isSmall: {
            type: Boolean,
            default: false
        }
    }
}
</script>
<template>
  <div class="logo">
    <img :class="['logo__img', isSmall ? 'logo__img_small-size' : '' ]" src="/assets/svg/logo.svg" alt="logo" />
    <h1 :class="['logo__title', isSmall ? 'logo__title_font-small' : '' ]">brix <span>templates</span></h1>
  </div>
</template>

<style lang="scss" scoped>
.logo {
  display: flex;
  align-items: center;
  gap: 16px;
  &__img {
    width: 40px;
    height: 40px;
    &_small-size {
      width: 34px;
      height: 34px;
    }
  }
  &__title {
    font-size: 36px;
    color: #170f49;
    font-weight: 900;
    &_font-small {
      font-size: 32px;
    }
    & span {
      color: #4a3aff;
    }
  }
}
</style>
