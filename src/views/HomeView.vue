<template>
  <div class="users-container">
    <div
      v-if="users && users.length"
      class="users"
    >
      <ul class="users-container">
        <li
          v-for="user in users"
          :key="user.id"
          class="user"
        >
          <h4>{{ user.name }}</h4>
          <p>Idade: {{ calculateAge(user.birthdate) }}</p>
        </li>
      </ul>
    </div>
    <div v-else-if="users.length === 0">
      <p class="without-results">Nenhum usuário cadastrado. Experimente começar pela página de cadastro.</p>
    </div>
    <LoadingPage
      v-else
      key="loading"
    />
  </div>
</template>

<script>
import { api } from "@/services.js";

export default {
  name: "HomeView",
  data() {
    return {
      users: null,
    };
  },
  methods: {
    calculateAge(apiDate) {
      let currentDate = new Date();
      let birthDate = new Date(apiDate);
      let difference = currentDate - birthDate;
      let age = Math.floor(difference / 31557600000);
      return age;
    },
  },
  async created() {
    document.title = "Users List";
    await api.get("/users").then((r) => {
      this.users = r.data;
    });
  },
};
</script>

<style scoped>
.users-container {
  max-width: 80%;
  margin: 50px auto;
}

.user {
  background: #fff;
  border-radius: 4px;
  box-shadow: 0 4px 8px rgba(30, 60, 90, 0.1);
  padding: 10px;
  transition: all 0.2s;
  margin: 15px 0;
}
.user:hover {
  box-shadow: 0 6px 12px rgba(30, 60, 90, 0.2);
  transform: scale(1.1);
  z-index: 1;
}

.without-results {
  text-align: center;
}

.name {
  margin-bottom: 10px;
  text-align: center;
}
</style>