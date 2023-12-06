<script>
import Button from './Button.vue'
import Inputs from './Inputs.vue'
import Radio from './Radio.vue'
import CheckboxMultiple from './CheckboxMultiple.vue'
export default {
  components: {
    Button,
    Inputs,
    Radio,
    CheckboxMultiple,
  },
  props: {
    formInfo: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {

      name: '',
      email: '',
      phone: '',
      company: '',
      inputForm: false,

      stepsProgressive: {
        steps: { 1: true, 2: false, 3: false, 4: false },
        step: ['1', '2', '3', '4'],
        currentStep: 1,
      },

      services: [
        {
          label: 'Development',
          id: 'development',
          checked: false,
        },
        {
          label: 'Marketing',
          id: 'marketing',
          checked: false,
        },
        {
          label: 'Web Design',
          id: 'web-design',
          checked: false,
        },
        { label: 'Other', id: 'other', checked: false },
      ],
      servicesChecked: [],
         prices: [
      {quantity: '$5.000 - $10.000', id: 'p1'},
      {quantity: '$10.000 - $20.000', id: 'p2'},
      {quantity: '$20.000 - $50.000', id: 'p3'},
      {quantity: '$50.000 +', id: 'p4'},
      ],
    selectedPriceValue: '' 
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
    setCheckboxValue: function (value, arr) {
      const index = arr.indexOf(value)
      if (index !== -1) {
        arr.splice(index, 1)
      } else {
        arr.push(value)
      }
      console.log('выполнено')
      return arr
    },
    selectedPrice: function (value, oldValue) {
      if(typeof value === 'String') {
        oldValue = value
        console.log(oldValue, 'TYT')
      }
     
    }
  },
}
</script>
<template>
  <div class="form">
    <div class="form-block">
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
         v-for="info in formInfo" :key="info.id"
      >
        <img
          class="form-block__contact-details__img"
          src="/assets/svg/form-submit.svg"
          alt="submit"
          v-if="info.id === 'submit'"
        />
        <h2 class="form-block__contact-details__title">
          {{info.title}}
        </h2>
        <span class="form-block__contact-details__text">{{info.subtitle}}</span>
        <div class="button-form__submit" v-if="info.id === 'submit' && this.stepsProgressive.currentStep === '4'">
          <Button label="Submit" />
        </div>

        <div class="form-block__slots">
          <div v-if="info.id === 'input'">
            <Inputs
          v-model:enterText.trim="name"
          name="Name"
          placeholder="John Carter"
          inputForm
        >
          <img width="20" height="25"  src="/assets/svg/inputs/user.svg" alt="user" />
        </Inputs>
      <Inputs
          v-model:enterText.trim="email"
          name="Email"
          placeholder="Email address"
          inputForm
        >
          <img width="20" height="25" src="/assets/svg/inputs/email.svg" alt="email" />
        </Inputs>
        <Inputs
          v-model:enterText.trim="phone"
          name="Phone Number"
          placeholder="(123) 456 - 7890"
          inputForm
        >
          <img width="20" height="25"  src="/assets/svg/inputs/phone.svg" alt="phone" />
        </Inputs>
        <Inputs
          v-model:enterText.trim="company"
          name="Company"
          placeholder="Company name"
          inputForm
        >
          <img width="20" height="25"  src="/assets/svg/inputs/company.svg" alt="company" />
        </Inputs>
          </div>
       
          <CheckboxMultiple
          v-if="info.id === 'checkbox' "
          name="servicesN"
          v-model:value="servicesChecked"
          :services="services"
          @checkbox="setCheckboxValue"
           />
           <div v-for="price in prices" :key="price.id"
            v-if="info.id === 'radio'">
            <Radio
            :value="price.quantity"
            :label="price.quantity"
            :id="price.id"
            name="price"
            v-model:oldValue="selectedPriceValue"
            @update="selectedPrice" />
          </div>
       
        </div>
      </div>
    </div>

    <div class="form-buttons">
      <Button label="Previous step" lightButton @click="previousStep" />
      <Button label="Next step"
       @click="nextStep" 
      />
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
      // margin-top: 40px;
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
