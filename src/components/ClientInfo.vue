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

    <div>
      <label>Дата рождения</label>
      <input
        type="date"
        @change="($event) => updateLastName($event, formAttributes.birthDate)"
      />
    </div>

    <FormSelector
      label="Пол"
      :list="gender"
      :handleChange="($event) => updateLastName($event, formAttributes.gender)"
    />

    <FormSelector
      label="Группа Клиентов"
      :isMultiple="true"
      :list="clientGroup"
      :handleChange="
        ($event) => updateLastName($event, formAttributes.clientGroup)
      "
    />
  </div>
</template>

<script>
import TextInput from "./FormElements/TextInput.vue";
import FormSelector from "./FormElements/FormSelector.vue";
import formAttributes from "../formAttributes";

export default {
  name: "ClientInfo",
  data() {
    return {
      gender: [
        {
          id: 0,
          value: "Мужчина",
        },
        { id: 1, value: "Женщина" },
      ],
      clientGroup: [
        { id: 0, value: "VIP" },
        { id: 1, value: "Проблемные" },
        { id: 2, value: "ОМС" },
      ],
      treatingDoctors: [
        { id: 0, value: "Иванов" },
        { id: 1, value: "Захаров" },
        { id: 2, value: "Чернышева" },
      ],
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
    FormSelector,
  },
};
</script>
