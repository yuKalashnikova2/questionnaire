<script>
export default {
 props: {
    enterText: {
      type: String,
      required: false,
    },
    placeholder: {
      type: String,
      default: 'Enter...',
    },
    name: {
      type: String,
      required: false,
    },
    inputForm: {
        type: Boolean,
        required: false
    },
    isWidth: {
      type: Boolean, 
      required: false
    }
  },
  emits: ['update:enterText'],
}
</script>

<template>
  <div :class="['input', inputForm  ? 'input_padding-top' :'' ]">
    <label class="input__label" :for="name">{{ name }}</label>
    <div :class="['input__enter', isWidth ? 'input__enter_width' : '']">
      <input
        type="text"
        :name="name"
        :placeholder="placeholder"
        :value="enterText"
        
      />
      <slot></slot>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.input {
  display: flex;
  flex-direction: column;
  &__label {
    color: var(--neutral-800, #170f49);
    font-feature-settings: 'clig' off, 'liga' off;
    font-size: 18px;
    font-weight: 500;
    line-height: 20px;
    margin-bottom: 17px;
  }
  &__enter {
    display: flex;
    justify-content: space-between;
    padding: 20px;
    border-radius: 46px;
    border: 1px solid var(--neutral-300, #eff0f6);
    background: var(--neutral-100, #fff);
    box-shadow: 0px 2px 6px 0px rgba(19, 18, 66, 0.07);
    color: var(--neutral-600, #6f6c90);
    font-size: 18px;
    font-weight: 400;
    line-height: 20px;
    &_width {
      min-width: 500px;
      @media (max-width: 575px) {
        min-width: 100%;
      }
    }
  }
}
</style>
