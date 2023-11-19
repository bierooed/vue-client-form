<template>
  <div>
    <label>Не отправлять СМС</label>
    <input type="checkbox" @change="handleChange" />
  </div>
</template>

<script>
export default {
  name: "FormCheckbox",
  props: {
    label: String,
    handleChange: Function,
  },
};
</script>
