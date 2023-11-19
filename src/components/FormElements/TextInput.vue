<template>
  <div>
    <label>{{ label }}</label>
    <input @change="handleChange" type="text" :placeholder="placeholder" />
  </div>
</template>

<script>
export default {
  name: "TextInput",
  props: {
    label: String,
    handleChange: Function,
    placeholder: String,
  },
};
</script>
