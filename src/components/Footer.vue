<script>
import Logo from './Logo.vue'
import Button from './Button.vue'
import Inputs from './Inputs.vue'
export default {
  components: {
    Logo,
    Button,
    Inputs
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
      <Inputs placeholder="Enter your email" isWidth>
        <Button label="Subscribe" smallSize />
    </Inputs>
  
    </div>
  </div>
</template>

<style lang="scss" scoped>
.footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 57px 0;
  @media (max-width: 992px) {
    flex-direction: column;
  }

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
