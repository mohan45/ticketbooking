<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <GetTicket msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import GetTicket from "@/components/GetTicket.vue";

export default {
  name: "Home",
  components: {
    GetTicket,
  },
};
</script>
