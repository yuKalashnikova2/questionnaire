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
      formInfo: [
        {
          title: 'Contact details',
          subtitle: 'Lorem ipsum dolor sit amet consectetur adipisc.',
          id: 'input',
          step: 1,
        },
        {
          title: 'Our services',
          subtitle: 'Please select which service you are interested in.',
          id: 'checkbox',
          step: 2,
        },
        {
          title: 'What’s your project budget?',
          subtitle: 'Please select the project budget range you have in mind.',
          id: 'radio',
          step: 3,
        },
        {
          title: 'Submit your quote request',
          subtitle:
            'Please review all the information you previously typed in the past steps, and if all is okay, submit your message to receive a project quote in 24 - 48 hours.',
          id: 'submit',
          step: 4,
        },
      ],
      selectedPriceValue: '',
    }
  },
  methods: {},
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
  @media (max-width: 575px) {
    margin: 0 10px;
  }
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
