<template>
  <v-container>
    <v-card
      v-if="
        paymentStatus === 'Credit' ||
          paymentStatus === 'Failed' ||
          orderId != ''
      "
      class="ma-auto my-10 pb-5"
      max-width="900"
      outlined
    >
      <v-row>
        <v-col cols="12" md="6">
          <v-card-text>
            <div class="logo">
              <span class="capitalletter">B</span>ooking
              <span class="capitalletter">D</span>etails
            </div>
          </v-card-text>
        </v-col>
        <v-col cols="12" md="6">
          <div class="order-block">
            <v-card-text
              class="d-flex justify-end font-weight-bold text-caption py-0"
              >Need help with your Trip?</v-card-text
            >
            <v-card-text
              class="d-flex justify-end font-weight-light text-caption py-0"
              >9999999999</v-card-text
            >
            <v-card-text
              class="d-flex justify-end font-weight-light text-caption py-0"
              >xyz@busbooking.com</v-card-text
            >
          </div>

          <div class="contact  ml-4 font-weight-light text-caption py-0">
            <div class="font-weight-bold">Need help with your Trip?</div>
            <div>9999999999</div>
            <div>xyz@busbooking.com</div>
          </div>
        </v-col>

        <!-- <v-col cols="12" md="8">
          <v-card-text>
            <div class="logo">
              <span class="capitalletter">B</span>ooking
              <span class="capitalletter">D</span>etails
            </div>
          </v-card-text>
        </v-col>
        <v-col cols="12" md="4">
          <v-card-text
            class="d-flex justify-end font-weight-bold text-caption py-0"
            >Need help with your Trip?</v-card-text
          >
          <v-card-text
            class="d-flex justify-end font-weight-light text-caption py-0"
            >9999999999</v-card-text
          >
          <v-card-text
            class="d-flex justify-end font-weight-light text-caption py-0"
            >xyz@busbooking.com</v-card-text
          >
        </v-col> -->
      </v-row>
      <v-divider class="mx-4"></v-divider>

      <v-row>
        <v-col cols="12" md="6">
          <v-card-text>
            <!-- <div>
          {{ selectedBooking.selectedSource }} ->
          {{ selectedBooking.selectedDestination }}
          <span class="date">{{
            selectedBooking.journeyDate
          }}</span>
          </div> -->
            <!-- <div> -->
            <div style="font-weight: 600; font-size: 14px;">
              {{ selectedBooking.source
              }}<span> <v-icon medium>mdi-arrow-right </v-icon></span>
              <span>{{ selectedBooking.destination }}</span>
            </div>
            <div>
              <span>{{ selectedBooking.journeyDate }}</span>
            </div>
            <!-- </div> -->
          </v-card-text>
        </v-col>
        <v-col cols="12" md="6">
          <div class="order-block">
            <v-card-text class="d-flex font-weight-light text-caption py-0"
              >OrderId: {{ selectedBooking.orderId }}</v-card-text
            >
            <v-card-text class="d-flex font-weight-light text-caption py-0"
              >Email: {{ selectedBooking.user.email }}</v-card-text
            >
            <v-card-text class="d-flex font-weight-light text-caption py-0"
              >Ph: {{ selectedBooking.user.contactNumber }}</v-card-text
            >
          </div>
          <div class="order ml-4 font-weight-light text-caption py-0">
            <div>OrderId: {{ selectedBooking.orderId }}</div>
            <div>Email: {{ selectedBooking.user.email }}</div>
            <div>Ph: {{ selectedBooking.user.contactNumber }}</div>
          </div>
        </v-col>
      </v-row>
      <v-divider cols="12" class="mx-4 py-1"></v-divider>
      <v-row>
        <v-col cols="12" md="12">
          <v-card-text>
            <v-simple-table>
              <template v-slot:default>
                <thead>
                  <tr>
                    <th class="text-left" style="font-size: 14px;color: black;">
                      Pick up
                    </th>
                    <th class="text-left" style="font-size: 14px;color: black;">
                      Drop
                    </th>
                    <th class="text-left" style="font-size: 14px;color: black;">
                      Time
                    </th>
                    <th class="text-left" style="font-size: 14px;color: black;">
                      Route Status
                    </th>
                    <th class="text-left" style="font-size: 14px;color: black;">
                      Total
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <td>{{ selectedBooking.source }}</td>
                    <td>{{ selectedBooking.destination }}</td>
                    <td>{{ selectedBooking.journeyTime }}</td>
                    <td>{{ selectedBooking.selectedRouteStatus }}</td>
                    <td>{{ selectedBooking.totalBusFare }} €</td>
                  </tr>
                </tbody>
              </template>
            </v-simple-table>
          </v-card-text>
        </v-col>
      </v-row>
      <!-- <v-row>
        <v-col cols="12" md="8">
          <v-card-text>
            <v-simple-table>
              <template v-slot:default>
                <thead>
                  <tr>
                    <th class="text-left">Name</th>
                    <th class="text-left">Gender</th>
                    <th class="text-left">Age</th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="passenger in selectedBooking.passengerList"
                    :key="passenger"
                  >
                    <td>{{ passenger.name }}</td>
                    <td>{{ passenger.gender }}</td>
                    <td>{{ passenger.age }}</td>
                  </tr>
                </tbody>
              </template>
            </v-simple-table>
          </v-card-text>
        </v-col>
      </v-row> -->
      <v-divider cols="12" class="mx-4"></v-divider>
      <v-row>
        <v-col cols="12" md="3">
          <v-card-text>
            <v-simple-table>
              <template v-slot:default>
                <thead>
                  <tr>
                    <th class="text-left">Passenger Name List</th>
                    <!-- <th class="text-left">Gender</th>
                      <th class="text-left">Age</th> -->
                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="passenger in selectedBooking.passengerList"
                    :key="passenger"
                  >
                    <td>{{ passenger.name }}</td>
                    <!-- <td>{{ passenger.gender }}</td>
                      <td>{{ passenger.age }}</td> -->
                  </tr>
                </tbody>
              </template>
            </v-simple-table>
          </v-card-text>
        </v-col>
      </v-row>
      <v-divider cols="12" class="mx-4"></v-divider>
      <v-row>
        <v-col cols="12" md="9">
          <v-card-text class="text-regular py-0"
            >NOTE: Always carry ticket printout and your ID proof while
            travelling.</v-card-text
          >
        </v-col>
        <v-col cols="12" md="3">
          <v-card-text class="d-flex justify-end font-weight-black py-0"
            ><span class="font-weight-light text-regular py-0"
              >Total Fare:</span
            >
            € {{ selectedBooking.totalBusFare }}</v-card-text
          >
        </v-col>
      </v-row>
      <!-- <div class="button-container pt-5">
          <div class="payment" @click="initiatePayment()">Payment</div>
        </div> -->
      <!-- Payment popup -->
      <!-- <v-row>
        <v-dialog
          v-model="paymentDialog"
          origin="center center"
          transition="dialog-bottom-transition"
          max-width="400"
          persistent
          overlay-opacity="0.99"
          overlay-color="#6f4a8e"
        >
          <v-card>
            <v-card-title
              v-if="paymentStatus === 'Credit'"
              class="headline pb-0"
              align="center"
              >Transaction Successful</v-card-title
            >
            <v-card-title
              v-if="paymentStatus === 'Failed'"
              class="headline pb-0"
              align="center"
              >Transaction Failed</v-card-title
            >
            <v-card-text class="py-0" v-if="paymentStatus === 'Credit'">
              <svg
                class="checkmark"
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 52 52"
              >
                <circle
                  class="checkmark__circle"
                  cx="26"
                  cy="26"
                  r="25"
                  fill="none"
                />
                <path
                  class="checkmark__check"
                  fill="none"
                  d="M14.1 27.2l7.1 7.2 16.7-16.8"
                />
              </svg>
            </v-card-text>
            <v-card-text
              class="headline red--text py-10"
              v-if="paymentStatus === 'Failed'"
              >Failed</v-card-text
            >
            <v-card-text class="text-caption py-0">PAYMENT DETAILS</v-card-text>
            <v-card-text class="py-0">
              <v-row>
                <v-col cols="12" sm="6">
                  <v-card-text class="d-flex font-weight-bold text-caption py-0"
                    >Payment ID</v-card-text
                  >
                </v-col>
                <v-col cols="12" sm="6">
                  <v-card-text
                    class="d-flex font-weight-light text-caption py-0"
                  >
                    {{ paymentId }}</v-card-text
                  >
                </v-col>
              </v-row>
            </v-card-text>
            <v-divider class="mx-4"></v-divider>
            <v-card-text class="py-0">
              <v-row>
                <v-col cols="12" sm="6">
                  <v-card-text class="d-flex font-weight-bold text-caption py-0"
                    >Payment Status</v-card-text
                  >
                </v-col>
                <v-col cols="12" sm="6">
                  <v-card-text
                    class="d-flex font-weight-light text-caption py-0"
                  >
                    {{ paymentStatus }}</v-card-text
                  >
                </v-col>
              </v-row>
            </v-card-text>
            <v-divider class="mx-4"></v-divider>
            <v-card-text class="py-0">
              <v-row>
                <v-col cols="12" sm="6">
                  <v-card-text class="d-flex font-weight-bold text-caption py-0"
                    >Name</v-card-text
                  >
                </v-col>
                <v-col cols="12" sm="6">
                  <v-card-text
                    class="d-flex font-weight-light text-caption py-0"
                  >
                    {{ selectedBooking.passengerList[0].name }}</v-card-text
                  >
                </v-col>
              </v-row>
            </v-card-text>
            <v-divider class="mx-4"></v-divider>
            <v-card-text class="py-0" v-if="paymentStatus === 'Credit'">
              <v-row>
                <v-col cols="12" sm="6">
                  <v-card-text class="d-flex font-weight-bold text-caption py-0"
                    >Paid</v-card-text
                  >
                </v-col>
                <v-col cols="12" sm="6">
                  <v-card-text
                    class="d-flex font-weight-light text-caption py-0"
                  >
                    € {{ selectedBooking.totalBusFare }}</v-card-text
                  >
                </v-col>
              </v-row>
            </v-card-text>
            <v-card-actions class="d-flex justify-end pt-4">
              <v-btn
                v-if="paymentStatus === 'Credit'"
                color="rgb(111, 74, 142)"
                @click="proceedToView()"
                >ProceedToView</v-btn
              >
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-row> -->
    </v-card>

    <!-- OrderId Input -->
    <!-- <v-row>
        <v-dialog
          v-model="orderDialog"
          origin="center center"
          transition="dialog-bottom-transition"
          max-width="400"
          persistent
        >
          <v-card>
            <v-card-title class="headline pb-0" align="center"
              >Order details</v-card-title
            >
            <v-col cols="12">
              <div class="label-heading">Track Id</div>
              <v-text-field
                solo
                label="Order Id"
                type="type"
                v-model="orderId"
                color="rgb(32, 106, 93)"
                prepend-inner-icon="mdi-bus-side"
              ></v-text-field>
            </v-col>
            <v-card-actions class="d-flex justify-end pt-4">
              <v-btn class="white--text" color="rgb(111, 74, 142)" @click="initializeOrder()"
                >View Order</v-btn
              >
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-row> -->
    <v-snackbar v-model="snackbar" :timeout="snachBarTimeout">
      {{ snackBarText }}
      <v-btn color="blue" text @click="snackbar = false">
        Close
      </v-btn>
    </v-snackbar>
  </v-container>
</template>

<script>
// import { orderService } from "../services/OrderService";
// import moment from "moment";

export default {
  name: "BookingPreviewPage",

  data: () => ({
    snackbar: false,
    snackBarText: "",
    snachBarTimeout: 3000,
    selectedBooking: {},
    passengerList: [],
    paymentDialog: false,
    orderDialog: false,
    paymentText: "",
    paymentId: String,
    paymentStatus: "Credit" | "Failed",
    paymentRequestId: String,
    orderId: ""
  }),

  created() {
    if (this.$route.query.payment_id) {
      // console.log("welcome order check");
      this.paymentId = this.$route.query.payment_id;
      this.paymentStatus = this.$route.query.payment_status;
      this.paymentRequestId = this.$route.query.payment_request_id;
      if (this.paymentStatus && this.paymentId) {
        // console.log("payment success status", this.paymentStatus);
        // this.orderDialog = false;
        this.respondToPayment();
        this.initializeBooking();
      }
    } else if (this.$route.query.orderId) {
      // this.orderDialog = true;
      this.orderId = this.$route.query.orderId;
      console.log("else order ID", this.$route.query.orderId);
      this.initializeOrder();
    }
  },
  methods: {
    initializeBooking() {
      let body = {
        criteria: {
          paymentId: this.paymentId,
          paymentRequestId: this.paymentRequestId
        }
      };
      orderService.getOrder(body).then(response => {
        console.log("booking data", response.data);
        this.selectedBooking = response.data;
        // this.paymentDialog = false;
        let date = new Date(response.data.journeyDate);
        this.selectedBooking.journeyDate = moment(date).format(
          "dddd, MMMM DD YYYY"
        );
        this.selectedBooking.passengerList.map(passanger => {
          this.passengerList.push(passanger);
        });
      });
      // this.selectedBooking.passengerList.map(passanger => {
      //   this.passengerList.push(passanger);
      // });
    },
    initializeOrder() {
      let body = {
        criteria: {
          orderId: this.orderId
        }
      };
      orderService.getOrder(body).then(response => {
        if (!response.data) {
          // this.orderDialog = true;
          this.snackbar = true;
          this.snackBarText = "Enter correct order Id";
          this.$router.push("/");
        } else {
          // this.orderDialog = false;
          this.selectedBooking = response.data;
          // this.paymentDialog = false;
          let date = new Date(response.data.journeyDate);
          this.selectedBooking.journeyDate = moment(date).format(
            "dddd, MMMM DD YYYY"
          );
        }
      });
      this.selectedBooking.passengerList.map(passanger => {
        this.passengerList.push(passanger);
      });
    },
    respondToPayment() {
      if (this.paymentStatus === "Credit") {
        console.log("successful payment");
        this.paymentDialog = true;
        // this.orderDialog = false;
        this.paymentText = "Your payment successfully completed";
      }
      if (this.paymentStatus === "Failed") {
        console.log("failed payment");
        this.paymentDialog = true;
        // this.orderDialog = false;
        this.paymentText =
          "Your payment was Failed. Please try again to booking your order.";
      }
    },
    proceedToView() {
      this.paymentDialog = false;
    }
  }
};
</script>
<style lang="scss" scoped>
.logo {
  font-weight: bolder;
  font-size: 20px;
  color: #e6683c;
  .capitalletter {
    font-size: 26px;
    color: #bc1888;
  }
}
.headline {
  color: #bc1888;
  text-align: center;
}
.failed {
  text-align: center;
  font-size: 22px;
  font-weight: bold;
  color: red;
}
.date {
  font-size: 14px;
  padding-left: 10px;
}
.button-container {
  display: flex;
  justify-content: center;
  .payment {
    background-color: #5f5864;
    color: #fff;
    font-size: 18px;
    font-weight: bold;
    padding: 10px 24px;
    display: flex;
    font-weight: bold;
    border: 1px solid #ddd;
    justify-content: center;
    text-transform: uppercase;
    width: 50%;
  }
}
.button-container:hover {
  cursor: pointer;
}
.avatar {
  border-radius: unset;
}
.checkmark__circle {
  stroke-dasharray: 166;
  stroke-dashoffset: 166;
  stroke-width: 2;
  stroke-miterlimit: 10;
  stroke: #7ac142;
  fill: none;
  animation: stroke 0.6s cubic-bezier(0.65, 0, 0.45, 1) forwards;
}

.checkmark {
  width: 56px;
  height: 56px;
  border-radius: 50%;
  display: block;
  stroke-width: 2;
  stroke: #fff;
  stroke-miterlimit: 10;
  margin: 10% auto;
  box-shadow: inset 0px 0px 0px #7ac142;
  animation: fill 0.4s ease-in-out 0.4s forwards,
    scale 0.3s ease-in-out 0.9s both;
}

.checkmark__check {
  transform-origin: 50% 50%;
  stroke-dasharray: 48;
  stroke-dashoffset: 48;
  animation: stroke 0.3s cubic-bezier(0.65, 0, 0.45, 1) 0.8s forwards;
}

@keyframes stroke {
  100% {
    stroke-dashoffset: 0;
  }
}
@keyframes scale {
  0%,
  100% {
    transform: none;
  }
  50% {
    transform: scale3d(1.1, 1.1, 1);
  }
}
@keyframes fill {
  100% {
    // box-shadow: inset 0px 0px 0px 30px #7ac142;
    box-shadow: inset 0px 0px 0px 30px #7ac142;
  }
}
// http://localhost:8080/#/order?payment_id=MOJO0925S05A56404739&payment_status=Credit&payment_request_id=54ba8d1217e548b4a9dc221947f8b098
@media screen and (min-width: 968px) {
  .order {
    top: 90px;
  }
}
@media screen and (min-width: 320px) and (max-width: 680px) {
  .order-block {
    display: none;
  }
}
@media screen and (min-width: 700px) {
  .order {
    position: absolute;
    top: 115px;
    right: 24px;
    font-size: 12px;
    text-align: right;
  }
  .contact {
    position: absolute;
    top: 15px;
    right: 24px;
    font-size: 12px;
    text-align: right;
  }
  .order-block {
    display: none;
  }
}
</style>
