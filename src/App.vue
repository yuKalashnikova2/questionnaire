<script>
import Header from './components/Header.vue'
import Form from './components/Form.vue'
import Footer from './components/Footer.vue'
import Inputs from './components/Inputs.vue'
export default {
  components: {
    Header,
    Form,
    Footer,
    Inputs,
  },
  data() {
    return {
      name: '',
      email: '',
      phone: '',
      company: '',
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
      <Form>
        <Inputs
          v-model:enterText.trim="name"
          name="Name"
          placeholder="John Carter"
        >
          <img src="/assets/svg/inputs/user.svg" alt="user" />
        </Inputs>
        <Inputs
          v-model:enterText.trim="email"
          name="Email"
          placeholder="Email address"
        >
          <img src="/assets/svg/inputs/email.svg" alt="email" />
        </Inputs>
        <Inputs
          v-model:enterText.trim="phone"
          name="Phone Number"
          placeholder="(123) 456 - 7890"
        >
          <img src="/assets/svg/inputs/phone.svg" alt="phone" />
        </Inputs>
        <Inputs
          v-model:enterText.trim="company"
          name="Company"
          placeholder="Company name"
        >
          <img src="/assets/svg/inputs/company.svg" alt="company" />
        </Inputs>
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
