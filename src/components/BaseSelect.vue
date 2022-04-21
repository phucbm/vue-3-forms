<template>
  <label :for="uuid" v-if="label">{{ label }}</label>
  <select
      v-bind="{
        ...$attrs,
        onChange: ($event) => {
          $emit('update:modelValue',$event.target.value)
        }
      }"
      :value="modelValue"
      class="field"
      :id="uuid"
  >
    <option
        v-for="option in options"
        :value="option"
        :key="option"
        :selected="option === modelValue"
    >{{ option }}
    </option>

  </select>
</template>

<script>
import UniqueID from "@/features/UniqueId";

export default {
  name: "BaseSelect",
  props: {
    label: {
      type: String,
      default: ''
    },
    modelValue: {
      type: [String, Number],
      default: ''
    },
    options: {
      type: Array,
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