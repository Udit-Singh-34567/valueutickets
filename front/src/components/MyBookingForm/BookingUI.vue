<template>
  <div class="container1">
    <!-- Header -->
    <div class="headerup">
      <h1>Booking Confirmed</h1>
      <p class="subheading">Good Option!! Shivam.</p>
      <p>Your flight is confirmed! Time to pack your bags!</p>
    </div>

    <div class="reference">
      <h2>Your Agency Reference Number</h2>
      <p class="ref-number">{{ bookingDetails.agency_reference_number }}</p>
      <button class="download-btn">Download Confirmation Ticket</button>
    </div>
  </div>

  <div class="container2">
    <!-- Main Content Section -->
    <div class="content">
      <div class="container">
        <h3 class="Main-heading">Review Your Itinerary</h3>
        <div class="header2">
          <button class="hide-details" @click="toggleDetails">
            {{ detailsVisible ? 'Hide Details' : 'Show All' }}
            <span class="circle">&or;</span>
          </button>
        </div>

        <!-- Conditionally render the itinerary card -->
        <div v-if="detailsVisible" class="itinerary-card">
          <div class="flight-info">
            <div class="route">
              <div class="super-saver">Time <span class="saver">Saver</span></div>
              <div class="from">
                <strong class="CityName">{{ bookingDetails.departure_iata }}</strong>
                <p class="Date">{{ bookingDetails.departure_date }}</p>
              </div>
              <<div class="flight-path">
                <div class="icon">✈️</div>
                <div class="dotted-line"></div>
                <div class="destination-point"></div>
              </div>
              <div class="to">
                <strong class="CityName">{{ bookingDetails.arrival_iata }}</strong>
                <p class="Date">{{ bookingDetails.arrival_date }}</p>
              </div>
            </div>

            <div class="flightdetails">
              <a href="#"><span>Flight Details</span></a>
              <span class="circle">&or;</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Passenger Details Section -->
      <div class="passenger-container">
        <div class="passenger-details">
          <div class="icon-heading">
            <span class="icon1">🚶‍♂️</span>
            <h2>Passengers Details</h2>
          </div>

          <div class="passenger-card" v-for="(passenger, index) in bookingDetails.passenger" :key="index">
            <p class="passenger-title">Passenger {{ index + 1 }}: <strong>{{ passenger.age >= 18 ? 'Adult' : 'Infant' }}</strong></p>
            <div class="details">
              <div>
                <p class="label">Name</p>
                <p class="value">{{ passenger.name }}</p>
              </div>
              <div>
                <p class="label">DOB</p>
                <p class="value">{{ passenger.dob }}</p>
              </div>
              <div>
                <p class="label">Gender</p>
                <p class="value">{{ passenger.gender }}</p>
              </div>
              <div>
                <p class="label">Type</p>
                <p class="value">{{ passenger.age >= 18 ? 'Adult' : 'Infant' }}</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Hotel Offer Section -->
        <div class="hotel-offer">
          <img src="@/assets/support.jpg" alt="Hotel Offer" class="offer-image" />
          <div class="offer-text">
            <p class="offer-heading">Booked Flight. Now save up to 20% on hotels too.</p>
            <p class="offer-subtext">✈️ Booked your flight? Now save up to 20% on hotels! Enjoy great deals on stays in Denver.</p>
          </div>
          <button class="interested-btn">Interested</button>
        </div>
      </div>

      <!-- Contact & Billing Details Section -->
      <div class="Contactcontainer">
        <div class="section">
          <div class="icon-heading">
            <span class="icon1"> 💳</span>
            <h2>Contact & Billing Details</h2>
          </div>
          <div class="details-card">
            <div class="details-left">
              <div class="info">
                <p class="label">Email</p>
                <p class="value">{{ bookingDetails.contact_billings.Email }}</p>
              </div>
              <div class="info">
                <p class="label">Contact Number</p>
                <p class="value">{{ bookingDetails.contact_billings.phone_number }}</p>
              </div>
              <div class="info">
                <p class="label">Card Type</p>
                <p class="value">{{ bookingDetails.contact_billings.card_type }}</p>
              </div>
            </div>
            <div class="details-right">
              <div class="info">
                <p class="label">Cardholder Name</p>
                <p class="value">{{ bookingDetails.contact_billings.cardholder_name }}</p>
              </div>
              <div class="info">
                <p class="label">Card Number</p>
                <p class="value">{{ bookingDetails.contact_billings.card_number }}</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Terms & Conditions Section -->
        <div class="section">
          <h2>Terms & Conditions</h2>
          <div class="terms-card">
            <p class="terms-text">
              Lorem Ipsum is simply dummy text of the printing and typesetting industry. 
              Lorem Ipsum has been the industry's standard dummy text ever since the 1500s...
            </p>
          </div>
        </div>
      </div>
    </div>

    <!-- Sidebar with Latest News -->
    <div class="sidebar">
      <div class="sidebarcontainer">
        <!-- Payment Summary Card -->
        <div class="payment-card">
          <div class="payment-header">
            <span class="payenticon">$</span>
            <span class="title">Payment</span>
          </div>
          <div class="payment-details">
            <div class="row">
              <span>Adult x 1</span>
              <span>$282.96</span>
            </div>
            <div class="row">
              <span>Base Fare</span>
              <span>$212.96</span>
            </div>
            <div class="row">
              <span>Taxes & Fees</span>
              <span>$82.96</span>
            </div>
            <div class="row">
              <span>SMS Fee</span>
              <span>$3.16</span>
            </div>
            <hr />
            <div class="row total">
              <span>Total</span>
              <span class="usd">USD 164.18</span>
            </div>
          </div>
          <p class="note">
            Rates are quoted in US dollars. Total amount may be charged in multiple transactions. 
            Grand total remains the same. Lorem ipsum dolor sit amet. 
          </p>
        </div>

        <!-- Need Help Section -->
        <div class="help-section">
          <h4>Need Help</h4>
          <div class="help-item">
            <span class="icon1">📞</span> 
            <span>+184 609 8899</span>
          </div>
          <div class="help-item">
            <span class="icon1">📧</span> 
            <span>support@flight.com</span>
          </div>
          <div class="help-button">✈️ Easy Booking</div>
          <div class="help-button">💬 24*7 Customer support</div>
          <div class="help-button">🔒 100% Safe & Secure</div>
          <div class="help-button">🏷️ Best Price Guarantee</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BookingConfirmation",
  props: {
    bookingDetails: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      detailsVisible: true, // Initially, the details are visible
    };
  },
  methods: {
    toggleDetails() {
      this.detailsVisible = !this.detailsVisible; // Toggle the visibility
    },
  },
};
</script>


<style scoped>

.container1 {
  max-width: 100%;
  margin: 20px auto;
  padding: 0px 20px;
  /* background-color: #00a37f; */
 
}

/* Header Styling */
.headerup {
  background-color: #007bff;
  color: white;
  text-align: center;
  padding: 15px;
  border-radius: 10px;
}

/* Reference Section */
.reference {
  text-align: center;
  margin: 20px 0;
 

}

.ref-number {
  font-size: 24px;
  font-weight: bold;
  color: #28a745;
  
}

.download-btn {
  background-color: #28a745;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 14px;
  border-radius: 5px;
  cursor: pointer;
}

/* Content and Layout */

.container2 {
  display: flex;
  gap: 30px;
  padding: 0 20px;
  width: 100%;
  max-width: 100%;
 
  
}

.content {
  flex: 1;
  /* background-color: violet; */
  /* margin-top: 20px; */
}

/* Itinerary Card */
.itinerary-card {
  background: white;
  border-radius: 15px;
  padding: 30px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
  border-top: 45px solid #00c896;
 
}

.Main-heading {
  margin-bottom: -1rem;
  font-weight: bold;
  font-size: 24px;
}

/* Toggle Button */
.header2 {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  margin-bottom: 1rem;
}

.hide-details {
  background: none;
  border: none;
  color: #5366ae;
  cursor: pointer;
  display: flex;
  align-items: center;
  font-weight: bold;
  gap: 5px;
}

.route {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 15px;
  border-bottom: 1px solid black;
 
}



.super-saver {
color: #00c896;
/* font-weight: bold; */
margin-bottom: 10px;
font-size: 18px;
display: inline-block;


}

.saver {
display: block;
font-size: 26px;
font-weight: bold;
}


/* Flight Path */

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
    left: calc(100% - 15px);
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

/* Flight Details Section */
.flightdetails {
  display: flex;
  gap: 8px;
  font-family: Arial, sans-serif;
 
}

.flightdetails a {
  text-decoration: none;
  color: blue;
  font-size: 16px;
}

/* Circular Button */
.circle {
  display: inline-flex;
   
  width: 20px;
  height: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  background-color: #007bff;
  color: black;
  font-size: 14px;
  text-align: center;
  /* margin-top: 5px; */
  text-decoration: none;

}

/* component 4 */

.passenger-container {
  max-width: 100%;
  margin: 20px auto;
  background-color: #f9f3f1;
  padding: 0 20px;
  border-radius: 10px;
}

/* Passenger Details */
.passenger-details {
  background: white;
  padding: 15px;
  border-radius: 10px;
}

/* Icon with Heading */
.icon-heading {
  display: flex;
  gap: 8px;
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 10px;
}

/* Passenger Card */
.passenger-card {
  background: #fff;
  padding: 15px;
  border-radius: 10px;
  /* box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1); */
}

.passenger-title {
  font-size: 16px;
  font-weight: bold;
  margin-bottom: 10px;
}


.details {
  display: flex; 
  flex-wrap: wrap; 
  gap: 20px; 
  justify-content: space-between; 
}

/* Labels & Values */
.label {
  font-size: 12px;
  color: gray;
}

.value {
  font-size: 14px;
  font-weight: bold;
}

/* Hotel Offer Section */
.hotel-offer {
  background: white;
  display: flex;
  align-items: center;
  gap: 20px;
  padding: 15px;
  border-radius: 10px;
  margin-top: 15px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
  margin-top: 20px;
}

/* Offer Image */
.offer-image {
  width: 200px;
  height: 160px;
  border-radius: 5px;
 
}

/* Offer Text  */
 /* .offer-text {
  flex: 1; 

} */

.offer-heading {
  font-size: 20px;
  font-weight: bold;
}

.offer-subtext {
  font-size: 18px;
  color: gray;
}

/* Interested Button */
.interested-btn {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 50px;
  border-radius: 5px;
  cursor: pointer;
  text-align: center;
  justify-items: center;
  margin-top: auto;
}

.interested-btn:hover {
    background-color: #0056b3;
    transform: scale(1.05);
}

/* last componenet */
/* Container */
.Contactcontainer {
  max-width: 100%;
  margin: 20px auto;
  background-color: #f9f3f1;
  padding: 0 20px;
  border-radius: 10px;
}

/* Section Headers */
.section {
  margin-bottom: 20px;
}

h2 {
  font-size: 18px;
  font-weight: bold;
}

/* Icon Heading */
.icon-heading {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 10px;
}

/* Card Styles */
.details-card {
  display: flex;
  justify-content: space-between;
  background: white;
  padding: 15px;
  border-radius: 10px;
}

.details-left, .details-right {
  width: 48%;
}

.info {
  margin-bottom: 10px;
}

.label {
  font-size: 12px;
  color: gray;
}

.value {
  font-size: 14px;
  font-weight: bold;
}

/* Terms & Conditions */
.terms-card {
  background: white;
  padding: 15px;
  border-radius: 10px;
}

.terms-text {
  font-size: 14px;
}

/* Sidebar */
.sidebar {
  width: 25%;
  /* padding-right: 30px; */
  /* background-color: #00a37f; */
}

  /* Container */
.sidebarcontainer {
  max-width: 100%;
  /* margin: 20px auto; */
  /* background-color: #f9f3f1; */
  /* padding: 20px; */
  border-radius: 10px;
 
}

/* Payment Card */
.payment-card {
  background: white;
  padding: 15px;
  border-radius: 10px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
 
}

.payment-header {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 10px;
  text-align: center;
  background-color: #96e3ef;
  padding:0 10px;
  border-radius: 5px;
}

.payment-details .row {
  display: flex;
  justify-content: space-between;
  margin: 5px 0;
}
.payenticon
{
  font-size: 25px;
}

.total {
  font-weight: bold;
  font-size: 16px;
}

.usd {
  color: black;
  font-weight: bold;
}
.payment-details hr {
  border: none; 

}



.total {
  font-weight: bold;
  font-size: 16px;
  border-top: 1px dotted black;
  border-bottom: 1px dotted black;
  padding: 8px 0; 
}

.note {
  font-size: 12px;
  color: gray;
  margin-top: 10px;
  text-align: center;
}

/* Help Section */
.help-section {
  margin-top: 20px;
}


h4{
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 10px;
  text-decoration: underline !important;
  text-decoration-color: black; /* Fixes the underline color */
  line-height: 1.3; 
  text-underline-offset: 4px;
  
}

.help-item {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 14px;
  margin-bottom: 8px;

}

.help-button {
  background: white;
  padding: 10px;
  border-radius: 10px;
  font-size: 14px;
  font-weight: bold;
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 15px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
  cursor: pointer;
}

.icon1 {
  font-size: 20px; /* Adjusted icon size */
  color: #007bff;
}



/* Media Queries for Responsiveness */
@media (max-width: 768px) {

  .container2 {
    flex-direction: column;
    width: 100%;
    /* gap: 70px; */
  }
  .itinerary-card {
    padding: 15px; /* Reduce padding for tablets */
  }

  .Main-heading {
    font-size: 22px; /* Adjust font size for tablets */
  }

  .saver {
    font-size: 24px; /* Adjust font size for tablets */
  }

  .flightdetails {
    font-size: 16px; /* Adjust font size for tablets */
  }

  .dotted-line {
    max-width: 150px; /* Adjust dotted line width for tablets */
  }

  .hotel-offer {
    flex-direction: row;
  }

  .interested-btn {
    width: auto;
    padding: 5px 20px;
  }

  .details-card {
    flex-direction: row;
  }

  .details-left, .details-right {
    width: 100%;
  }

  .sidebar {
    width: 100%;
    padding: 0 25px;
  }
}

@media (max-width: 480px) {
  
  .route {
    flex-direction: column; /* Stack vertically on tablets */
  }
  
  .super-saver {
    font-size: 14px;
  }

  .saver {
    font-size: 20px;
  }

  .CityName {
    font-size: 14px;
  }

  .Date {
    font-size: 10px;
  }

  .flightdetails {
    font-size: 14px;
  }

  .dotted-line {
    max-width: 150px; /* Adjust dotted line width for phones */
  }

  .icon {
    font-size: 20px; /* Adjust icon size for phones */
  }

  .circle {
    width: 18px;
    height: 18px;
    font-size: 12px;
  }
  
  .Main-heading {
    font-size: 20px;
  }

  .saver {
    font-size: 22px;
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
  /* margin-bottom: 8px; */
}

.icon {
  position: absolute;
  left: 0;
  animation: move-plane 3s linear infinite;
  font-size: 15px;
  margin-left: 5px;
}

  .flightdetails {
    font-size: 16px;
  }

  /* card detals */
  .details-card {
    flex-direction: column; /* Stack elements */
    align-items: center;
    text-align: center;
    /* padding: 15px; */
  }

  .details-left,
  .details-right {
    width: 100%; /* Full width */
  }

  .label {
    font-size: 1.1em; 
   
  }

  .value {
    font-size: 1em;
    word-break: break-word;
  }


  /*    */

  .offer-heading {
    font-size: 18px;
  }

  .offer-subtext {
    font-size: 16px;
  }

  .help-button {
    font-size: 12px;
  }

  .hotel-offer {
    flex-direction: column;
  }
  .sidebar {
    width: 100%;
    padding: 0 25px;
  }
}


/* ✅ Styles for screens 360px and below */
@media (max-width: 360px) {
  .hide-details
  {
    margin-top: 20px;
    
  }
 
}

</style>
