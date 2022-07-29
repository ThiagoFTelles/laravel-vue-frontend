<template>
  <nav>
    <router-link
      to="/"
      class="home"
    >Home</router-link>
    <router-link
      class="btn"
      to="/register"
    >
      Cadastrar
    </router-link>
  </nav>
</template>

<script>
export default {
  name: "TheHeader",
};
</script>

<style scoped>
nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px 20px;
  box-shadow: 0 2px 2px 4px rgba(30, 60, 90, 0.1);
}

.home {
  padding: 10px 0;
}
</style>