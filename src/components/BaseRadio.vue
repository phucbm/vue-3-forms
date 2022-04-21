<template>
  <input
      type="radio"
      :checked="modelValue === value"
      :value="value"
      @change="$emit('update:modelValue', value)"
      v-bind="$attrs"
      :id="uuid"
  />
  <label :for="uuid" v-if="label">{{ label }}</label>
</template>

<script>
import UniqueID from "@/features/UniqueId";

export default {
  name: "BaseRadio",
  props: {
    label: {
      type: String,
      default: ''
    },
    modelValue: {
      type: [String, Number],
      default: false
    },
    value: {
      type: [String, Number],
      required: true
    }
  },
  setup(){
    const uuid = UniqueID();
    return {uuid}
  }
}
</script>

<style scoped>

</style>