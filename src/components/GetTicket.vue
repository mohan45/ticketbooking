<template>
  <v-container>
    <v-row class="text-center" align="center">
      <v-col cols="12" class="my-2">
        GET TICKET
      </v-col>
      <v-col cols="12">
        Enter your details, and Check your tickets 
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="4" align-self="center">
        <v-text-field
          label="Name"
          :rules="rules"
          hide-details="auto"
        ></v-text-field>
        <v-text-field label="Phone Number"></v-text-field>
      </v-col>
    </v-row>
    <v-row justify="center">
        <v-btn
          color="primary"
        >
          <span class="mr-2">Get Ticket</span>
        </v-btn>
      <!-- </v-col> -->

    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "GetTicket",

  data: () => ({
    headers: [
      {
        text: 'Bus Name',
        align: 'start',
        // sortable: false,
        value: 'name',
      },
      { text: 'UserName', value: 'username' },
      { text: 'Seat No', value: 'seatnumber' },
      { text: 'Ticket No', value: 'ticketnumber' },
      { text: 'Phone No', value: 'phonenumber' },
    ],
    desserts: [
      {
        name: 'Kpn',
        username: 'Mohan',
        seatnumber: 14,
        ticketnumber: 23,
        phonenumber: 9944769004
      },
      {
        name: 'Parveen',
        username: 'Prabu',
        seatnumber: 5,
        ticketnumber: 45,
        phonenumber: 9944839812
      },
    ]
  }),
};
</script>
