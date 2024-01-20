<template>
  <div>
    <button @click="loginWithGoogle">Login</button>
  </div>
</template>

<script>
import axios from "axios";

export default {

  methods: {
    loginWithGoogle() {
      axios
        .get("http://127.0.0.1:8000/api/auth/google")
        .then((response) => {
          const redirectUrl = response.data.url;
          if (redirectUrl) {
  
            window.location.href = redirectUrl;
          } else {
            console.error("Unexpected response format:", response.data);
          }
        })
        .catch((error) => {
          console.error("Error making the request:", error);
        });
    },
  },
};
</script>
