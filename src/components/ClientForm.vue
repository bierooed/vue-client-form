<template>
  <div>
    Client form
    {{ client.lastName }} - {{ client.firstName }} - {{ client.middleName }} -
    {{ client.birthDate }} - {{ client.gender }}
    <ClientInfo :client="client" @update-client="updateClient" />
  </div>
</template>

<script>
import ClientInfo from "./ClientInfo.vue";
export default {
  name: "ClientForm",
  data() {
    return {
      client: {
        gender: "Мужчина",
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
