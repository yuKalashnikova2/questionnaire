<script>
export default {
  props: {
    label: {
      type: String,
      required: false,
    },
    id: {
      type: String,
      default: '',
    },
    checked: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<template>
  <label :class="['checkbox', checked ? 'checkbox_checked' : '']">
    <div class="checkbox__input">
      <input type="checkbox" :id="id" :checked="checked" />
      <img :src="'/assets/svg/checkbox/' + id + '.svg'" :alt="id" />
    </div>

    <div>{{ label }}</div>
  </label>
</template>

<style lang="scss" scoped>
.checkbox {
  display: flex;
  align-items: center;
  gap: 23px;
  padding: 23px 25px;
  border-radius: 16px;
  width: 284px;
  background: var(--neutral-100, #fff);
  box-shadow: 0px 4px 10px 0px rgba(31, 37, 89, 0.07),
    0px 2px 11px 0px rgba(69, 65, 164, 0.06);
  color: var(--neutral-800, #170f49);
  font-feature-settings: 'clig' off, 'liga' off;
  font-size: 18px;
  font-weight: 500;
  line-height: 20px;
  border: 1px solid transparent;
  cursor: pointer;
  &_checked {
    border: 1px solid var(--primary-color-1, #4a3aff);
  }
  &__input {
    width: 66px;
    height: 66px;
    background-color: #d6d3f8;
    border-radius: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
