<script setup>

import { ref } from "vue";
import { useAuthStore } from "../stores/auth";

const authStore = useAuthStore();

const form = ref({
    email: "",
    password: "",
});

</script>
<template>
   <div>
 <form  @submit.prevent="authStore.handleLogin(form)">
    @CSRF
  <label for="fname">First name:</label><br>
  <input type="email" id="fname" name="fname" v-model="form.email" value="John"><br>
  <div v-if="authStore.errors.email" class="flex">
    <span class="text-red-400 text-sm m-2 p-2">{{
         authStore.errors.email[0]
    }}</span>
</div>
  <label for="lname">Last name:</label><br>
  <input type="password" id="lname" name="lname" v-model="form.password" value="Doe"><br><br>
  <div v-if="authStore.errors.password" class="flex">
   <span class="text-red-400 text-sm m-2 p-2">{{
    authStore.errors.password[0]
    }}</span>
   </div>
  <input type="submit" value="Submit">
</form> 
<router-link to="/forgot-password" class="text-primary hover:underline">
 Forgot Password?
</router-link>

   </div> 
</template>