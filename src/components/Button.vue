<script>
export default {
  props: {
    label: {
      type: String,
      default: 'Button',
    },
    smallSize: {
        type: Boolean,
        required: false
    },
    lightButton: {
        type: Boolean, 
        required: false
    }
  },
  emits: {

  }
}
</script>
<template>
  <button :class="['button', smallSize ? 'button_button-small' : '', lightButton ? 'button_previous': '']">{{ label }}</button>
</template>

<style lang="scss" scoped>
.button {
  padding: 20px 40px;
  border-radius: 56px;
  background: #4a3aff;
  border: none;
  color: #fff;
  text-align: center;
  font-size: 18px;
  font-weight: 700;
  line-height: 20px;
  cursor: pointer;
  &_button-small {
    padding: 14px 26px;
    font-size: 16px;
    font-weight: 500;
    line-height: 18px;
  }
  &_previous {
    font-weight: 400;
    background-color: #fff;
    color: #4A3AFF;
    border-radius: 66px;
    border: 1px solid var(--primary-color-1, #4A3AFF);  
  }
}
</style>
