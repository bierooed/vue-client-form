<template>
  <div>
    <label>{{ label }}</label>
    <select :multiple="isMultiple" @change="handleChange">
      <option v-for="list in list" :key="list.id">
        {{ list.value }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "FormSelector",

  props: {
    label: String,
    isMultiple: Boolean,
    list: Array,
    handleChange: Function,
  },
};
</script>
