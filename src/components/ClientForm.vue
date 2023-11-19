<template>
  <div>
    Client form
    {{ client.lastName }} - {{ client.firstName }} - {{ client.middleName }} -
    {{ client.birthDate }} - {{ client.gender }} -
    {{ client.treatingDoctors }}

    <p v-if="client.sms">Do not send SMS</p>
    <ClientInfo :client="client" @update-client="updateClient" />
  </div>
</template>

<script>
import formAttributes from "@/formAttributes";
import ClientInfo from "./ClientInfo.vue";
export default {
  name: "ClientForm",
  data() {
    return {
      client: {
        [formAttributes.gender]: "Мужчина",
        [formAttributes.treatingDoctors]: "Иванов",
      },
    };
  },

  methods: {
    updateClient(updatedClient) {
      console.log("Heyyy");
      this.client = { ...this.client, ...updatedClient };
    },
  },
  components: {
    ClientInfo,
  },
};
</script>
