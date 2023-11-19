<template>
  <div>
    Client info
    <TextInput
      label="Last Name"
      placeholder="Last Name"
      :handleChange="
        ($event) => updateLastName($event, formAttributes.lastName)
      "
    />

    <TextInput
      label="First Name"
      placeholder="First Name"
      :handleChange="
        ($event) => updateLastName($event, formAttributes.firstName)
      "
    />

    <TextInput
      label="Middle Name"
      placeholder="Middle Name"
      :handleChange="
        ($event) => updateLastName($event, formAttributes.middleName)
      "
    />
  </div>
</template>

<script>
import TextInput from "./FormElements/TextInput.vue";
import formAttributes from "../formAttributes";

export default {
  name: "ClientInfo",
  data() {
    return {
      formAttributes,
    };
  },
  props: {
    client: Object,
  },
  methods: {
    updateLastName(e, key) {
      console.log("updated");
      this.$emit("update-client", { [key]: e.target.value });
    },
  },

  components: {
    TextInput,
  },
};
</script>
