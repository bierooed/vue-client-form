<template>
  <div>
    Client info
    <TextInput
      label="Last Name"
      placeholder="Last Name"
      :handleChange="($event) => updateLastName($event)"
    />
  </div>
</template>

<script>
import TextInput from "./FormElements/TextInput.vue";
export default {
  name: "ClientInfo",
  props: {
    client: Object,
  },
  methods: {
    updateLastName(e) {
      console.log("updated");
      this.$emit("update-client", { lastName: e.target.value });
    },
  },

  components: {
    TextInput,
  },
};
</script>
