<script>
export default {
  data() {
    return {
      picked: 'One',
    }
  },
  props: {
    value: {
      type: String,
      default: 'value',
    },
    label: {
      type: String,
      default: 'label',
    },
    id: {
      type: String,
      default: 'id',
    },
    name: {
      type: String,
    },
    oldValue: {
      type: String,
      default: '',
    },
    emit: ['update:checkedValue'],
    methods: {
      handleChecked: function () {
        emit('update:checkedValue', value, oldValue)
      },
    },
  },
}
</script>

<template>
  <label class="checkbox radio">
    <div
      :class="['radio__input', oldValue == value ? 'radio__input_checked' : '']"
    >
      <input
        type="radio"
        :name="name"
        :id="id"
        :value="value"
        @input="$emit('update:oldValue', value, oldValue)"
      />
      <div class="radio__input_checked__inside"></div>
    </div>

    <div class="radio__label">{{ label }}</div>
  </label>
</template>

<style lang="scss">
.radio {
  display: flex;
  gap: 12px;
  padding: 45px 0 45px 32px !important;
  &__input {
    flex-shrink: 0;
    width: 24px;
    height: 24px;
    stroke-width: 1.2px;
    stroke: #d9dbe9;
    box-shadow: 0px -3px 7px 0px rgba(20, 20, 43, 0.08) inset;
    border-radius: 100%;
    background-color: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    &_checked {
      background-color: #4a3aff;
      &__inside {
        background-color: #fff;
        width: 10px;
        height: 10px;
        border-radius: 100%;
      }
    }
  }
  &__label {
    color: #170f49;
    font-feature-settings: 'clig' off, 'liga' off;
    font-size: 18px;

    font-weight: 500;
    line-height: 20px;
  }
}
</style>
