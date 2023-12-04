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
  },
  emits: ['update: modelValue', 'checkbox'],
}
</script>
<template>
  <Checkbox
    v-for="service in services"
    :checked="value.includes(service.id)"
    :name="name"
    :label="service.label"
    :id="service.id"
    @click.prevent="$emit('checkbox', service.id, value)"
  />
</template>
