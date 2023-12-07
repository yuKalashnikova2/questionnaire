<script>
import Logo from './Logo.vue'
import Button from './Button.vue'
export default {
  components: {
    Button,
    Logo
  },
}
</script>
<template>
  <header class="header">
    <Logo />
    <Button label="Clone now" />
  </header>
</template>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  padding: 42px 0 45px 0;
  @media (max-width: 767px) {
    flex-direction: column;
    gap: 15px;
  }
}
</style>
