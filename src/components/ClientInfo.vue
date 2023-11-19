<template>
  <div>
    Client info
    <TextInput
      label="Last Name"
      placeholder="Last Name"
      :handleChange="
        ($event) => updateClientInfo($event, formAttributes.lastName)
      "
    />

    <TextInput
      label="First Name"
      placeholder="First Name"
      :handleChange="
        ($event) => updateClientInfo($event, formAttributes.firstName)
      "
    />

    <TextInput
      label="Middle Name"
      placeholder="Middle Name"
      :handleChange="
        ($event) => updateClientInfo($event, formAttributes.middleName)
      "
    />

    <div>
      <label>Дата рождения</label>
      <input
        type="date"
        @change="($event) => updateClientInfo($event, formAttributes.birthDate)"
      />
    </div>

    <FormSelector
      label="Пол"
      :list="gender"
      :handleChange="
        ($event) => updateClientInfo($event, formAttributes.gender)
      "
    />

    <!-- Add multiple input handling  -->
    <FormSelector
      label="Группа Клиентов"
      :handleChange="updateMultipleSelectors"
      :isMultiple="true"
      :list="clientGroup"
    />

    <FormSelector
      label="Лечащий врач"
      :list="treatingDoctors"
      :handleChange="
        ($event) => updateClientInfo($event, formAttributes.treatingDoctors)
      "
    />

    <FormCheckbox
      label="Не отправлять СМС"
      v-model="checkboxState"
      :handleChange="
        ($event) => updateCheckbox($event.target.checked, formAttributes.sms)
      "
    />
  </div>
</template>

<script>
import TextInput from "./FormElements/TextInput.vue";
import FormSelector from "./FormElements/FormSelector.vue";
import FormCheckbox from "./FormElements/FormCheckbox.vue";

import formAttributes from "../formAttributes";

export default {
  name: "ClientInfo",
  data() {
    return {
      checkboxState: false,
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
    updateClientInfo(e, key) {
      console.log("updated");
      this.$emit("update-client", { [key]: e.target.value });
    },

    updateCheckbox(isActive, key) {
      this.$emit("update-client", { [key]: isActive });
    },

    updateMultipleSelectors() {
      console.log("Not yet added handle function(");
    },
  },

  components: {
    TextInput,
    FormSelector,
    FormCheckbox,
  },
};
</script>
