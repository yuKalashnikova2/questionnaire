<script>
export default {
  props: {
    label: {
      type: String,
      default: 'Button',
    },
  },
  emits: {
    
  }
}
</script>
<template>
  <button class="button">{{ label }}</button>
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
}
</style>
