<template>
  <label :for="uuid" v-if="label">{{ label }}</label>
  <input
      v-bind="$attrs"
      :placeholder="label"
      class="field"
      :value="modelValue"
      @input="$emit('update:modelValue',$event.target.value)"
      :id="uuid"
  >
</template>

<script>
import UniqueID from "@/features/UniqueId";

export default {
  name: "BaseInput",
  props: {
    label: {
      type: String,
      default: ''
    },
    modelValue: {
      type: [String, Number],
      default: ''
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