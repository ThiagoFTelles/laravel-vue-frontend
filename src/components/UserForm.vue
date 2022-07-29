<template>
  <form>
    <label for="name">Nome:</label>
    <input
      type="text"
      id="name"
      name="name"
      v-model="name"
      maxlength="40"
      minlength="2"
      placeholder="Seu nome"
    />
    <label for="birthdate">Data de nascimento:</label>
    <input
      type="date"
      name="birthdate"
      v-model="birthdate"
      required
    >
    <button
      class="btn"
      @click.prevent="saveUser"
    >Salvar</button>
  </form>
</template>

<script>
import { api } from "@/services.js";

export default {
  data() {
    return {
      birthdate: null,
      name: "",
    };
  },
  methods: {
    async saveUser() {
      let user = {
        name: this.name,
        birthdate: this.birthdate,
      };
      try {
        await api
          .post("/users", user)
          .then((r) => {
            this.users = r.data;
          })
          .then(this.$router.push("/"));
      } catch {
        (e) => console.log(e);
      }
    },
  },
};
</script>

<style scoped>
</style>
