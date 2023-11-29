<script>
import Logo from './Logo.vue'
import Button from './Button.vue'
export default {
  components: {
    Logo,
    Button,
  },
  data() {
    return {
      isSmall: true,
    }
  },
}
</script>

<template>
  <div class="footer">
    <div class="footer__copyright">
      <Logo isSmall />
      <div class="footer__copyright-text"
        >Copyright © 2023 BRIX Templates | All Rights Reserved</div
      >
    </div>

    <div class="footer__subscribe">
      <input type="text" placeholder="Enter your email" />
      <Button />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.footer {
  display: flex;
  justify-content: space-between;
  padding: 57px 0;

  &__copyright {
 
    display: flex;
    flex-direction: column;
    gap: 16px;
    &-text {
      color: var(--neutral-600, #6f6c90);
      font-feature-settings: 'clig' off, 'liga' off;
      font-size: 18px;
      font-weight: 400;
      line-height: 30px;
    }
  }
  &__subscribe {
    display: flex;
  }
}
</style>
