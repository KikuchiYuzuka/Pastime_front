<template>
  <main class="form-signin">
    <form @submit.prevent="submit">
      <h1 class="h3 mb-3 fw-normal">Please register</h1>
      <div class="form-floating">
        <input v-model="first_name" class="form-control" placeholder="First Name">
        <label>First Name</label>
      </div>

      <div class="form-floating">
        <input v-model="last_name" class="form-control" placeholder="Last Name">
        <label>Last Name</label>
      </div>

      <div class="form-floating">
        <input v-model="email" type="email" class="form-control" placeholder="name@example.com">
        <label>Email address</label>
      </div>

      <div class="form-floating">
        <input v-model="password" type="password" class="form-control" placeholder="Password">
        <label>Password</label>
      </div>

      <div class="form-floating">
        <input v-model="password_confirm" type="password" class="form-control" placeholder="Password Confirm">
        <label>Password Confirm</label>
      </div>

      <button class="w-100 btn btn-lg btn-primary" type="submit">Submit</button>
    </form>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "Register",
  data() {
    return {
      first_name: '',
      last_name: '',
      email: '',
      password: '',
      password_confirm: ''
    }
  },
  methods: {
    async submit() {
      await axios.post('register', {
        first_name: this.first_name,
        last_name: this.last_name,
        email: this.email,
        password: this.password,
        password_confirm: this.password_confirm,
      });

      await this.$router.push('/login');
    }
  }
}
</script>
