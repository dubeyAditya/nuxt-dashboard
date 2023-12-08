<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const username = ref('');
const password = ref('');
const error = ref('');

const router = useRouter();

const login = () => {
  // In a real-world scenario, validate credentials with a server
  if (username.value === 'user' && password.value === 'password') {
    // Simulate a successful login
    localStorage.setItem('isLoggedIn', 'true');
    router.push('/dashboard');
  } else {
    error.value = 'Invalid credentials';
  }
};
</script>

<template>
    <v-row class="d-flex mb-3">
        <v-col cols="12">
            <v-label class="font-weight-bold mb-1">Username</v-label>
            <v-text-field v-model="username" variant="outlined" hide-details color="primary"></v-text-field>
        </v-col>
        <v-col cols="12">
            <v-label class="font-weight-bold mb-1">Password</v-label>
            <v-text-field v-model="password" variant="outlined" type="password"  hide-details color="primary"></v-text-field>
        </v-col>
        <v-col cols="12" class="pt-0">
            <div class="d-flex flex-wrap align-center ml-n2">
                <v-checkbox v-model="checkbox"  color="primary" hide-details>
                    <template v-slot:label class="text-body-1">Remeber this Device</template>
                </v-checkbox>
                <div class="ml-sm-auto">
                    <NuxtLink to="/"
                        class="text-primary text-decoration-none text-body-1 opacity-1 font-weight-medium">Forgot
                        Password ?</NuxtLink>
                </div>
            </div>
        </v-col>
        <v-col cols="12" class="pt-0">
            <v-btn @click="login" color="primary" size="large" block   flat>Sign in</v-btn>
        </v-col>
    </v-row>
</template>
