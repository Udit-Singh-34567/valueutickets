<template>
  <div class="container">
    <h3 class="Main-heading">Review Your Itinerary</h3>
    <div class="header">
      <button class="hide-details" @click="toggleDetails">
        {{ detailsVisible ? 'Hide Details' : 'Show All' }} <span class="dot"></span>
      </button>
    </div>
    <!-- Conditionally render the itinerary card based on detailsVisible -->
    <div v-if="detailsVisible" class="itinerary-card">
      <div class="flight-info">
        <div class="route">
          <div class="super-saver">GOOD<span class="saver">CHOICE</span></div>
          <div class="from">
            <strong class="CityName">{{ flightDetails.flight_name }}</strong>
            <p class="SRC">{{ flightDetails.src }}</p>
            <p class="Date">{{ formatDateTime(flightDetails.departure) }}</p>
          </div>
          <div class="flight-path">
            <div class="icon">✈️</div>
            <div class="dotted-line"></div>
            <div class="destination-point"></div>
          </div>
          <div class="to">
            <strong class="CityName">{{ flightDetails.destination_iata }}</strong>
            <p class="DEST">{{ flightDetails.dest }}</p>
            <p class="Date">{{ formatDateTime(flightDetails.arrival) }}</p>
          </div>
        </div>
        <hr class="separator">
        <div class="actions">
          <button class="call-now">Call now: +1 833-931-6548</button>
          <div class="price-info">
            <p class="Price-per-person">Flight Price</p>
            <span class="additional-info">(incl. Taxes & Fees)</span>
          </div>
          <div class="price">${{ flightDetails.price }}</div>
          <button class="book-now">Book Now</button>
        </div>
      </div>
    </div>
    <div class="contact-form">
    <h4 class="heading-contact-info">How do we contact you?</h4>
    <div class="info-box">
      <div class="inputs">
        <input
          type="text"
          v-model="phone_number"
          @input="updateContactInfo"
          placeholder="Phone Number *"
          required
          :class="{ 'invalid': phone_numberError }"
        />
        <span v-if="phone_numberError" class="error-message">Invalid phone number. Format: xxxxxxxxxx</span>
        
        <input
          type="email"
          v-model="email"
          @input="updateContactInfo"
          placeholder="Email *"
          required
          :class="{ 'invalid': emailError }"
        />
        <span v-if="emailError" class="error-message">Please enter a valid email address.</span>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
import { useRoute } from "vue-router";

export default {
  name: "FlightItinerary",
  data() {
    return {
      detailsVisible: true, // Initially, the details are visible
      phone_number: "",
      email: "",
      phone_numberError: false,
      emailError: false,
      flightDetails: {},
    };
  },
  methods: {
    updateContactInfo() {
      this.validateForm();
      this.$emit("update-contact", { email: this.email, phone_number: this.phone_number });
    },
    toggleDetails() {
      this.detailsVisible = !this.detailsVisible; // Toggle the visibility of the details
    },
    validateForm() {
      this.phone_numberError = !this.validatephone_number(this.phone_number);
      this.emailError = !this.validateEmail(this.email);
    },
    validatephone_number(phone) {
      // USA phone number regex: xxxxxxxxxx
      const phoneRegex = /^\d{10}$/;
      return phoneRegex.test(phone);
    },
    validateEmail(email) {
      // Basic email regex validation
      const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
      return emailRegex.test(email);
    },
    formatDateTime(dateTimeString) {
      if (!dateTimeString) return "N/A"; // Return a default value if the dateTimeString is undefined
      const date = new Date(dateTimeString);
      if (isNaN(date)) return "N/A"; // Return a default value if the date is invalid
      return new Intl.DateTimeFormat("en-US", {
        month: "short",
        day: "2-digit",
        year: "numeric",
        hour: "2-digit",
        minute: "2-digit",
        hour12: true,
      }).format(date);
    },
  },
  mounted() {
    const route = useRoute();
    this.flightDetails = route.query;
  },
  watch: {
    phone_number() {
      this.validateForm();
    },
    email() {
      this.validateForm();
    },
  },
};
</script>


<style scoped>
.container {
  font-family: Arial, sans-serif;
  padding: 20px;
  background: #EAF3F2;
  width:100%;
  max-width:100%;
}

.itinerary-card {
  background: white;
  border-radius: 15px;
  padding: 30px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
  border-top: 36px solid #00c896;
}

.Main-heading {
  margin-bottom: -1rem;
  font-weight: bold;
  font-size:24px;
}

.header {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  color: #333;
  margin-bottom: 1rem;
}

.hide-details {
  background: none;
  border: none;
  color: #5366AE;
  cursor: pointer;
  display: flex;
  align-items: center;
  font-weight: bold;
  animation: pulseAnimation 1.5s infinite;
}
.CityName{
  font-size:22px;
  font-weight:bold;
}
@keyframes pulseAnimation {
  0% {
    color: #5366AE;
    transform: scale(1);
  }
  50% {
    color:  #5366AE;
    transform: scale(1.1);
  }
  100% {
    color: #5366AE;
    transform: scale(1);
  }
}

.dot {
  width: 10px;
  height: 10px;
  background-color: #5366AE;
  border-radius: 50%;
  margin-left: 5px;
}

.super-saver {
  color: #00c896;
  font-weight: bold;
  margin-bottom: 10px;
  font-size: 22px;
  display: inline-block;
}

.saver {
  display: block;
  font-size: 26px;
}

.route {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 15px;
}

.flight-path {
  position: relative;
  display: flex;
  align-items: center;
  gap: 5px;
}

.dotted-line {
  border-top: 1px dashed #007bff;
  width: 200px;
}

.icon {
  position: absolute;
  left: 0;
  animation: move-plane 3s linear infinite;
  font-size: 24px;
  margin-left: 5px;
}

@keyframes move-plane {
  0% {
    left: 0;
  }
  50% {
    left: 50%;
    transform: translateX(-50%);
  }
  100% {
    left: calc(100% - 15px); /* Stop at the destination dot */
  }
}


.destination-point {
  position: absolute;
  left: 100%;
  transform: translateX(-50%);
  width: 12px;
  height: 12px;
  background-color: #007bff;
  border-radius: 50%;
  margin-top: -2px;
}

.to {
  text-align: right;
}

.separator {
  border: none;
  height: 1px;
  background-color: #ccc;
  margin: 15px 0;
}

.actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 15px;
  margin-top: 20px;
}

.call-now {
  background: #00c896;
  color: white;
  border: none;
  padding: 12px 18px;
  border-radius: 10px;
  cursor: pointer;
  font-weight: bold;
  transition: transform 0.3s ease, background 0.3s ease;
}

.call-now:hover {
  background: #00a37f;
  transform: scale(1.1);
}

.price-info {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-left: 10px;
}

.additional-info {
  font-size: 12px;
  color: #666;
  margin-top: -5px;
}

.book-now {
  background: linear-gradient(90deg, #3e41ec, #09c398);
  border: none;
  padding: 10px 20px;
  color: #fff;
  border-radius: 50px;
  cursor: pointer;
  transition: background 0.3s ease;
  margin-left: 20px;
  animation: pulse 1.5s infinite;
}

.price {
  font-size: 22px;
  color: #00c896;
  font-weight: bold;
  margin-left: 36rem;
}

@keyframes pulse {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.1);
  }
  100% {
    transform: scale(1);
  }
}

.book-now:hover {
  background: linear-gradient(90deg, #00ced1, #1e90ff);
  animation: bounce 0.6s ease;
}

@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-5px);
  }
}

.heading-contact-info {
  margin-bottom: 10px;
  font-weight: bold;
}

.info-box {
  background: white;
  border-radius: 15px;
  padding: 40px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
}

.inputs {
  display: flex;
  gap: 15px;
}

.inputs input {
  flex: 1;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 10px;
  font-size: 14px;
}

.invalid {
  border-color: red;
}

.error-message {
  color: red;
  font-size: 12px;
  margin-top: 5px;
}
/*---------------Responsiveness---------------------*/
@media (max-width: 1200px) {
  .container, .itinerary-card, .info-box {
    padding: 20px;
  }
  .price {
    margin-left: auto;
  }
}

@media (max-width: 768px) {
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 10px;
  }
 
  .itinerary-card, .header, .info-box {
    padding: 15px;
    width: 90%;
  }

  .route, .actions {
    flex-direction: column;
    align-items: center;
    gap: 20px;
    width: 100%;
  }

  .info-box {
    width: 80vw;
    padding: 20px;
  }
    .Main-heading {
    margin-top: 1.2rem; 
    margin-bottom: 0.3rem; 
    font-size: 24px;
  }

  .hide-details {
    margin-top: 0.2rem; /* Gap ko kam karne ke liye */
  }

  .inputs {
    flex-direction: column;
    align-items: center;
    gap: 15px;
    width: 100%;
    padding: 0 15px;
    box-sizing: border-box;
  }

  .inputs input {
    width: 100%;
    padding: 12px;
    font-size: 14px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 10px;
    box-sizing: border-box;
  }

  .call-now, .book-now {
    padding: 12px 20px;
    font-size: 16px;
    margin: 10px 0;
  }

  .price {
    margin: auto;
  }

  
}
</style>
