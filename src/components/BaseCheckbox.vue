<template>
  <input
      type="checkbox"
      :checked="modelValue"
      @change="$emit('update:modelValue', $event.target.checked)"
      class="field"
      :id="uuid"
  />
  <label :for="uuid" v-if="label">{{ label }}</label>
</template>

<script>
import UniqueID from "@/features/UniqueId";

export default {
  name: "BaseCheckbox",
  props: {
    label: {
      type: String,
      default: ''
    },
    modelValue: {
      type: Boolean,
      default: false
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