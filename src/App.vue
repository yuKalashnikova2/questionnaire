<script>
import Header from './components/Header.vue'
import Form from './components/Form.vue'
import Footer from './components/Footer.vue'
import Inputs from './components/Inputs.vue'
import CheckboxMultiple from './components/CheckboxMultiple.vue'
import Radio from './components/Radio.vue'
export default {
  components: {
    Header,
    Form,
    Footer,
    Inputs,
    Radio,
    CheckboxMultiple,
  
  },
  data() {
    return {
      name: '',
      email: '',
      phone: '',
      company: '',
      inputForm: false,
      formInfo: [
        {title: 'Contact details' , subtitle: 'Lorem ipsum dolor sit amet consectetur adipisc.', id: 'input'},
        {title: 'Our services' , subtitle: 'Please select which service you are interested in.',  id: 'checkbox'},
        {title: 'What’s your project budget?' , subtitle: 'Please select the project budget range you have in mind.',  id: 'radio'},
        {title: 'Submit your quote request' , subtitle: 'Please review all the information you previously typed in the past steps, and if all is okay, submit your message to receive a project quote in 24 - 48 hours.',  id: 'submit'},
      ],
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
  <div class="container">
    <Header />
    <div class="preview">
      <h1 class="preview__title">Get a project quote</h1>
      <div class="preview__text">
        Please fill the form below to receive a quote for your project. Feel
        free to add as much detail as needed.
      </div>

      <Form :formInfo="formInfo">
        <!-- <div v-for="price in prices" :key="price.id">
            <Radio
            :value="price.quantity"
            :label="price.quantity"
            :id="price.id"
            name="price"
            v-model:oldValue="selectedPriceValue"
            @update="selectedPrice"
            />
        </div> -->
        <!-- <CheckboxMultiple
          name="servicesN"
          v-model:value="servicesChecked"
          :services="services"
          @checkbox="setCheckboxValue"
        /> -->
        <!-- <Inputs
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
        </Inputs> -->
      </Form>
    </div>
  </div>

  <div class="gray-line"></div>

  <div class="container">
    <Footer />
  </div>
</template>

<style lang="scss">
.container {
  max-width: 1242px;
  margin: 0 100px;
}
.preview {
  margin: auto;
  max-width: 700px;
  text-align: center;

  &__title {
    color: #170f49;
    text-align: center;
    font-feature-settings: 'clig' off, 'liga' off;
    font-weight: 700;
    font-size: 34px;
    font-weight: 700;
    line-height: 46px;
  }
  &__text {
    max-width: 630px;
    color: #6f6c90;
    text-align: center;
    font-feature-settings: 'clig' off, 'liga' off;
    font-size: 18px;
    font-weight: 400;
    line-height: 30px;
    margin-top: 12px;
    margin-bottom: 42px;
  }
}
.gray-line {
  border-bottom: 1px solid #d9dbe9;
}
</style>
