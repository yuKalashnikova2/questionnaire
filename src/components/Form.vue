<script>
import Button from './Button.vue'
export default {
  components: {
    Button,
  },
  data() {
    return {
      stepsProgressive: {
        steps: { 1: true, 2: false, 3: false, 4: false },
        step: ['1', '2', '3', '4'],
        currentStep: 1,
      },
    }
  },

  methods: {
    nextStep() {
      this.stepsProgressive.currentStep++
      this.stepsProgressive.steps[this.stepsProgressive.currentStep] = true
    },
    previousStep() {},
    styleColor() {
      index + 1 == this.stepsProgressive.currentStep ? '' : 'disabled'
    },
  },
}
</script>
<template>
  <div class="form">
    <ul class="form__steps-list">
      <li
        class="form__steps-list__step"
        v-for="(step, index) in stepsProgressive.step"
      >
        <div
          :class="[
            'form__steps-list__step-bubble',
            stepsProgressive.steps[index + 1] ? '' : 'disabled',
          ]"
        >
          {{ step }}
        </div>
        <div class="form__steps-list__step-line">
          <div
            :class="[
              'form__steps-list__step-line-fill',
              stepsProgressive.steps[index + 1] ? '' : 'disabled',
            ]"
          ></div>
        </div>
      </li>
    </ul>

    <div class="form__contact-details">
      <h2 class="form__contact-details__title">Contact details</h2>
      <span class="form__contact-details__text"
        >Lorem ipsum dolor sit amet consectetur adipisc.</span
      >

      <div class="form__slots">
        <slot></slot>
      </div>
 
    </div>
  </div>
</template>

<style lang="scss" scoped>
.form {
  border-radius: 34px;
  border: 1px solid var(--neutral-300, #eff0f6);
  background: var(--neutral-100, #fff);
  box-shadow: 0px 5px 16px 0px rgba(8, 15, 52, 0.06);
  width: 100%;
//   height: 100vh;
  padding: 32px 46px 80px 46px;
  margin-bottom:100px;
  &__steps-list {
    display: flex;
    align-items: center;

    border-bottom: 1px solid #d9dbe9;
    padding-bottom: 33px;
    &__step {
      display: flex;
      align-items: center;

      &:last-child .form__steps-list__step-line {
        display: none;
      }
      &-bubble {
        width: 34px;
        height: 34px;
        background-color: #4a3aff;
        color: #fff;
        border-radius: 100%;
        font-size: 16px;
        font-weight: 400;
        line-height: 23px;
        display: flex;
        align-items: center;
        justify-content: center;
      }

      &-line {
        background-color: #eff0f6;
        width: 100px;
        height: 6px;
        border-radius: 40px;
        margin: 0 18px;

        &-fill {
          background-color: #4a3aff;
          height: 100%;
          border-radius: 40px;
          &_half {
            width: 50%;
          }
        }
      }
    }
  }
  &__contact-details {
    margin-top: 64px;
    // margin-bottom: 80px;
    text-align: start;
    &__title {
      color: #170f49;
      font-feature-settings: 'clig' off, 'liga' off;
      font-size: 24px;

      font-weight: 700;
      line-height: 35px;
    }
    &__text {
      margin: 7.5px 0 40px 0;
      color: #6f6c90;
      font-feature-settings: 'clig' off, 'liga' off;
      font-size: 18px;

      font-weight: 400;
      line-height: 30px;
    }
  }
  &__slots {
    display: flex;
    flex-wrap: wrap;
    gap: 28px;
    margin: auto;
  }
}

.disabled {
  background-color: #eff0f6;
  color: #6f6c90;
}
</style>
