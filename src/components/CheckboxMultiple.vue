<script>
import Checkbox from './Checkbox.vue'
export default {
  components: {
    Checkbox,
  },
  props: {
    value: {
      type: Array,
      required: true,
    },
    services: {
      type: Array,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    servicesChecked: {
      type: Array,
    },
  },
  data() {
    return {
      checkboxActive: false,
    }
  },
  emits: ['update: modelValue',
  'checkbox'],

}
</script>
<template>
  <Checkbox
    v-for="service in services"
    :checked="service.checked"
    :name="name"
    :label="service.label"
    :id="service.id"
    :value="service.value"
    :modelValue="service.checked"
    @click.prevent="$emit('checkbox', service.id, value )"
  />

  {{ servicesChecked }}
</template>

<style lang="scss"></style>
