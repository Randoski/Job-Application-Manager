<template>
  <div class="flex items-center justify-center h-screen px-6 bg-gray-200">
    <div class="w-full max-w-sm p-6 bg-white rounded-md shadow-md">
      <div class="flex items-center justify-center">
       
        <router-link
          to="/"
          class="text-pry self-center text-xl font-bold whitespace-nowrap"
          >TryJam</router-link
        >
      </div>

      <form class="mt-4" @submit.prevent="forgotPassword">
        <label class="block">
          <span class="text-sm text-gray-700">Email</span>
          <input
            v-model="email"
            type="email"
            class="block w-full mt-1 border-gray-200 rounded-md focus:border-pry"
          />
        </label>

        <div class="mt-6">
          <button
            type="submit"
            class="w-full px-4 py-2 text-sm text-center text-white bg-pry rounded-md focus:outline-none hover:bg-pry"
          >
            Reset Password
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import { getAuth, sendPasswordResetEmail } from "firebase/auth";

export default {
  data() {
    return {
      email: "",
    };
  },
  methods: {
    forgotPassword() {
      const auth = getAuth();
      sendPasswordResetEmail(auth, this.email).then(() => {});
      this.$router.push("/login");
      alert("An password reset link has been sent to your email").catch((error) => {
        const errorCode = error.code;
        const errorMessage = error.message;
        alert(errorCode, errorMessage);
      });
    },
  },
};
</script>
