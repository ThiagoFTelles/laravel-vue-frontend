<template>
  <section class="register">
    <h1>Novo Cadastro</h1>
    <UserForm />
  </section>
</template>

<script>
import UserForm from "@/components/UserForm.vue";

export default {
  name: "RegisterView",
  components: {
    UserForm,
  },
  data() {
    return {
      newUser: {
        name: "",
        birthdate: "",
      },
      erros: [],
    };
  },
  computed: {},
  methods: {
    saveUser() {},
  },
  created() {
    document.title = "Register";
  },
};
</script>

<style scoped>
.register {
  max-width: 500px;
  margin: 0 auto;
  padding: 0 20px;
}

h1 {
  text-align: center;
  font-size: 2rem;
  margin: 40px auto;
}

form {
  display: grid; /* Deixar um item em baixo do outro */
}

.btn {
  width: 100%;
  max-width: 300px;
  margin-left: auto;
  margin-right: auto;
}
</style> 
 