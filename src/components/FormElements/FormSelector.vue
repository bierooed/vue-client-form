<template>
  <select @change="handleChange">
    <option v-for="list in list" :key="list.id">
      {{ list.value }}
    </option>
  </select>
</template>

<script>
export default {
  name: "FormSelector",
  props: {
    list: Array,
    handleChange: Function,
  },
};
</script>
