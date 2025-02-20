<template>
  <div class="container my-4">
    <div class="card mx-auto" style="max-width: 500px;">
      <div class="icon-container text-center my-4">
        <img src="@/assets/logo-nobg.png" alt="Plane Icon" class="icon" />
      </div>
      <h2 class="text-center mb-4">Access Trip Itinerary</h2>
      <div class="form-container p-4">
        <div class="form-group">
          <label for="bookingId">Booking ID</label>
          <input v-model="bookingId" type="text" class="form-control" id="bookingId" placeholder="BookingID" />
        </div>
        <div class="form-group">
          <label for="email">Email ID</label>
          <input v-model="email" type="text" class="form-control" id="email" placeholder="Email ID" />
        </div>
        <button @click="searchBooking" class="btn btn-primary btn-block">Track Booking Status</button>
      </div>
    </div>

    <div v-if="bookingDetails" class="details-container">
      <h3>Booking Details</h3>
      <table class="table table-bordered table-responsive w-100">
        <tbody>
          <tr>
            <th>Flight Name</th>
            <td>{{ bookingDetails.flight_name }}</td>
          </tr>
          <tr>
            <th>Departure IATA</th>
            <td>{{ bookingDetails.departure_iata }}</td>
          </tr>
          <tr>
            <th>Arrival IATA</th>
            <td>{{ bookingDetails.arrival_iata }}</td>
          </tr>
          <tr>
            <th>Departure Date</th>
            <td>{{ formatDateTime(bookingDetails.departure_date) }}</td>
          </tr>
          <tr>
            <th>Arrival Date</th>
            <td>{{ formatDateTime(bookingDetails.arrival_date) }}</td>
          </tr>
        </tbody>
      </table>

      <h3>Passengers</h3>
      <table class="table table-bordered table-responsive w-100">
        <thead>
          <tr>
            <th>Name</th>
            <th>DOB</th>
            <th>Gender</th>
            <th>Age</th>
            <th>Type</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(passenger, index) in bookingDetails.passenger" :key="index">
            <td>{{ passenger.name }}</td>
            <td>{{ passenger.dob }}</td>
            <td>{{ passenger.gender }}</td>
            <td>{{ passenger.age }}</td>
            <td>{{ getPassengerType(passenger.age) }}</td>
          </tr>
        </tbody>
      </table>

      <h3>Contact & Billings</h3>
      <table class="table table-bordered table-responsive w-100">
        <tbody>
          <tr>
            <th>Email</th>
            <td>{{ bookingDetails.contact_billings.Email }}</td>
          </tr>
          <tr>
            <th>Phone Number</th>
            <td>{{ bookingDetails.contact_billings.phone_number }}</td>
          </tr>
          <tr>
            <th>Cardholder Name</th>
            <td>{{ bookingDetails.contact_billings.cardholder_name }}</td>
          </tr>
          <tr>
            <th>Card Number (Last 4 Digits)</th>
            <td>{{ bookingDetails.contact_billings.card_number }}</td>
          </tr>
        </tbody>
      </table>

      <h3>Orderings</h3>
      <table class="table table-bordered table-responsive w-100">
        <tbody>
          <tr v-if="bookingDetails.orderings.payble_amount">
            <th>Payable Amount</th>
            <td>{{ bookingDetails.orderings.payble_amount }}</td>
          </tr>
          <tr v-if="bookingDetails.orderings.flight_cancellation_protection">
            <th>Flight Cancellation Protection</th>
            <td>{{ bookingDetails.orderings.flight_cancellation_protection }}</td>
          </tr>
          <tr v-if="bookingDetails.orderings.sms_support">
            <th>SMS Support</th>
            <td>{{ bookingDetails.orderings.sms_support }}</td>
          </tr>
          <tr v-if="bookingDetails.orderings.baggage_protection">
            <th>Baggage Protection</th>
            <td>{{ bookingDetails.orderings.baggage_protection }}</td>
          </tr>
          <tr v-if="bookingDetails.orderings.premium_support">
            <th>Premium Support</th>
            <td>{{ bookingDetails.orderings.premium_support }}</td>
          </tr>
          <tr v-if="bookingDetails.orderings.total_refund_protection">
            <th>Total Refund Protection</th>
            <td>{{ bookingDetails.orderings.total_refund_protection }}</td>
          </tr>
          <tr v-if="bookingDetails.orderings.total_amount">
            <th>Total Amount</th>
            <td>{{ bookingDetails.orderings.total_amount }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import moment from 'moment-timezone';

export default {
  name: "LoginForBooking",
  data() {
    return {
      bookingId: '',
      email: '',
      bookingDetails: null,
    };
  },
  methods: {
    async searchBooking() {
      try {
        const response = await axios.post('https://crm.valueutickets.com/api/login/', {
          email: this.email,
          booking_id: this.bookingId,
        });
        this.bookingDetails = response.data;
      } catch (error) {
        console.error('Error:', error.response ? error.response.data.error : error.message);
      }
    },
    getPassengerType(age) {
      if (age < 2) return 'Infant';
      if (age < 12) return 'Child';
      return 'Adult';
    },
    formatDateTime(dateTime) {
      return moment(dateTime)
        .tz('America/New_York')
        .format('D MMM, YYYY [at] h:mm:ss A [America/New_York Timezone]');
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
}

.card {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.icon-container {
  margin-bottom: 20px;
  background-color: #f9f2f2;
}

.icon {
  width: auto;
  height: 100px;
}

.text-center {
  text-align: center;
}

.my-4 {
  margin-top: 1.5rem;
  margin-bottom: 1.5rem;
}

.mb-4 {
  margin-bottom: 1.5rem;
}

.p-4 {
  padding: 1.5rem;
}

.btn-block {
  display: block;
  width: 100%;
}

.form-container {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
}


.icon {
  width: auto;
  height: 100px;
}


.details-container {
  background: white;
  padding: 20px;
  margin-top:25px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.table-responsive {
  margin-top: 20px;
}

.table {
  width: 100%;
}
</style>
