<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        Ticket Booking
      </div>

      <v-spacer></v-spacer>

      <!-- <v-btn
      >
        <span class="mr-2">Upload Excel</span>
      </v-btn> -->
    </v-app-bar>

    <v-main>
      <GetTicket />
    </v-main>
  </v-app>
</template>

<script>
import GetTicket from "./components/GetTicket";

export default {
  name: "App",

  components: {
    GetTicket,
  },

  data: () => ({
    //
  }),
};
</script>
