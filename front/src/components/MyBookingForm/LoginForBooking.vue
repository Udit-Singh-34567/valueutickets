<template>
    <div class="container">
      <div class="icon-container">
        <img src="@/assets/logo-nobg.png" alt="Plane Icon" class="icon" />
      </div>
      <h2>Access Trip Itinerary</h2>
      <div class="form-container">
        <label>BookingID / PNR No.</label>
        <input type="text" placeholder="BookingID / PNR No." id="bookingId" />
        <label>Last Name</label>
        <input type="text" placeholder="Last Name" id="lastName" />
        <button onclick="searchBooking()">Search Booking</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "LoginForBooking",
    methods: {
      searchBooking() {
        const bookingId = document.getElementById('bookingId').value;
        const lastName = document.getElementById('lastName').value;
        alert(`Searching for Booking ID: ${bookingId} and Last Name: ${lastName}`);
      }
    }
  };
  </script>
  
  <style scoped>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 70dvh;
    background-color: #F9F2F2;
    padding: 20px;
  }
  
  h2 {
    font-size: 29px;
    font-weight: bold;
    margin-bottom: 20px;
  }
  
  .icon-container {
    margin-bottom: 20px;
    background-color: #F9F2F2;
  }
  
  .icon {
    width: auto;
    height: 100px;
  }
  
  .form-container {
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 100%;
    max-width: 500px;
  }
  
  label {
    display: block;
    font-size: 19px;
    margin-bottom: 5px;
  }
  
  input {
    width: 100%;
    font-size: 19px;
    padding: 20px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  button {
    font-size: 19px;
    width: 100%;
    background-color: #1d4ed8;
    color: white;
    padding: 10px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #1e40af;
  }
  </style>
  