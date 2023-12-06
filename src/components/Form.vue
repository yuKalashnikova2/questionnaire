<script>
import Button from './Button.vue'
export default {
  components: {
    Button,
  },
  props: {
    formInfo: {
      type: Array,
      required: true,
    },
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
    previousStep() {
      this.stepsProgressive.currentStep--
      if(this.stepsProgressive.steps[this.stepsProgressive.currentStep] !== '1' && this.stepsProgressive.steps[this.stepsProgressive.currentStep] !== '4') {
        this.stepsProgressive.steps[this.stepsProgressive.currentStep] = false
      }
      
    },
    styleColor() {
      index + 1 == this.stepsProgressive.currentStep ? '' : 'disabled'
    },
  },
}
</script>
<template>
  <div class="form">
    <div class="form-block" v-for="info in formInfo" :key="info.id">
      <ul class="form-block__steps-list">
        <li
          class="form-block__steps-list__step"
          v-for="(step, index) in stepsProgressive.step"
        >
          <div
            :class="[
              'form-block__steps-list__step-bubble',
              stepsProgressive.steps[index + 1] ? '' : 'disabled',
            ]"
          >
            {{ step }}
          </div>
          <div class="form-block__steps-list__step-line">
            <div
              :class="[
                'form-block__steps-list__step-line-fill',
                stepsProgressive.steps[index + 1] ? '' : 'disabled',
              ]"
            ></div>
          </div>
        </li>
      </ul>

      <div
        :class="[
          'form-block__contact-details',
          info.id === 'submit' ? 'form-block__contact-details_text-center' : '',
        ]"
      >
        <img
          class="form-block__contact-details__img"
          src="/assets/svg/form-submit.svg"
          alt="submit"
          v-if="info.id === 'submit'"
        />
        <h2 class="form-block__contact-details__title">{{ info.title }}</h2>
        <span class="form-block__contact-details__text">{{
          info.subtitle
        }}</span>
        <div class="button-form__submit" v-if="info.id === 'submit'">
          <Button label="Submit" />
        </div>

        <div class="form-block__slots">
          <slot></slot>
        </div>
      </div>
    </div>

    <div class="form-buttons">
      <Button label="Previous step" lightButton @click="previousStep" />
      <Button label="Next step" @click="nextStep" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.form {
  &-block {
    border-radius: 34px;
    border: 1px solid var(--neutral-300, #eff0f6);
    background: var(--neutral-100, #fff);
    box-shadow: 0px 5px 16px 0px rgba(8, 15, 52, 0.06);
    width: 100%;
    //   height: 100vh;
    padding: 32px 46px 80px 46px;
    margin-bottom: 32px;
    &__steps-list {
      display: flex;
      align-items: center;

      border-bottom: 1px solid #d9dbe9;
      padding-bottom: 33px;
      &__step {
        display: flex;
        align-items: center;

        &:last-child .form-block__steps-list__step-line {
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
      text-align: start;
      &_text-center {
        text-align: center;
      }
      &__img {
        width: 157px;
        height: 143px;
        padding-bottom: 18px;
        margin: auto;
      }
      &__title {
        color: #170f49;
        font-feature-settings: 'clig' off, 'liga' off;
        font-size: 24px;

        font-weight: 700;
        line-height: 35px;
      }
      &__text {
        // margin: 7.5px 0 40px;
        // padding-bottom: 40px ;
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
      // margin: auto;
      margin-top: 40px;
    }
  }
  &-buttons {
    display: flex;
    justify-content: space-between;
    margin-bottom: 100px;
  }
}

.disabled {
  background-color: #eff0f6;
  color: #6f6c90;
}
.button-form__submit {
  padding-top: 12px;
}
</style>
