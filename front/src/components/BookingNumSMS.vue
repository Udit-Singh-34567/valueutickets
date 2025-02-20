<template>
  <div class="container">
    <h3>Booking number by sms </h3>
    <div class="card">
      
      <!-- Header Section -->
      <div class="header">
        <!-- Left Side: Badge and Title -->
        <div class="header-left">
          <span class="badge">Recommended</span>
          <h2 class="title">Booking number by sms</h2>
        </div>

        <!-- Right Side: Icon -->
        <img src="@/assets/SMS.png" alt="Premium Support" class="icon" />
      </div>

      <!-- Description -->
      <div class="description">
        Skip the line and get easy access to expert assistance when you need it.
      </div>

      <!-- Support Options -->
      <div class="options">
        
        <!-- Premium Support Option -->
        <label 
          class="option" 
          :class="{ 'selected': selectedSupport === 'premium' }"
        >
          <div class="option-content">
            <div class="option-header">
              <!-- Left side: Radio button and title in one row -->
              <!-- Yes Option -->
              <label class="option-left">
                <input 
                  type="radio" 
                  name="sms" 
                  :checked="smsSupport" 
                  @change="updateSmsSelection(true)" 
                />
                <p class="option-title">Yes, I want SMS Support</p>
              </label>

              <!-- Right side: Price and "Per Person" text -->
              <div class="option-right">
                <p class="option-price">$2.00</p>
                <span class="persontext">Per Person</span>
              </div>
            </div>

            <ul class="option-list">
              <li>✔ Receive your booking nubers via SMS for easy assess</li>
              <li>✔ Store your trip info offline</li>
            
            </ul>

            <span class="read-more">
               <span class="read-more-text">Read More...</span>
               <span class="read-more-icon">&or;</span>
            </span>
          </div>
        </label>

        <!-- No Thanks Option -->
        <label 
          class="option" 
          :class="{ 'selected': selectedSupport === 'none' }"
        >
          <div class="option-content">
            <div class="option-header">
              <!-- Left side: Radio button and title in one row -->
              <!-- No Option -->
              <label class="option-left">
                <input 
                  type="radio" 
                  name="sms" 
                  :checked="!smsSupport" 
                  @change="updateSmsSelection(false)" 
                />
                <p class="option-title">No thanks</p>
              </label>
              <!-- Right side: Price and "Per Person" text -->
              <div class="option-right">
                <p class="option-price">$0.00</p>
              </div>
            </div>
          </div>
        </label>

        <!-- Disclaimer -->
        <p class="disclaimer">* Booking number by SMS is Non-Refundable Once Purchased</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      smsSupport: false, // Default: No SMS Support
    };
  },
  methods: {
    updateSmsSelection(value) {
      this.smsSupport = value;
      this.$emit("update-sms-support", value); // Emit value to parent
    }
  }
};
</script>


<style scoped>
/* Page container */
.container {
  background-color: #EAF3F2;
  /* padding: 20px; */
  width: 100%;
  max-width: 100%;
  /* bottom: 10px; */
}

h3 {
  padding: 10px 10px;
}

/* Card styling */
.card {
  background-color: white;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  width: 100%;
  overflow: hidden;
  border-radius: 12px;
}

/* Header section */
.header {
  background-color: #4B4DC8;
  padding: 10px 30px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-radius: 12px 12px 0 0;
}

/* Left-side container */
.header-left {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 5px;
}

/* Badge styling */
.badge {
  background-color: #4ACFFF;
  color: white;
  font-size: 14px;
  padding: 6px 12px;
  border-radius: 12px;
  font-weight: normal;
  margin-left: 20px;
}

/* Title styling */
.title {
  font-size: 20px;
  font-weight: bold;
  color: white;
}

/* Icon styling */
.icon {
  width: 160px;
  height: 120px;
  border-radius: 8px;
}

/* Description */
.description {
  padding: 10px;
  font-size: 16px;
  color: black;
  border-radius: 10px;
  background-color: #EAFAF8;
  margin: 16px;
  width: 95%;
}

/* Options */
.options {
  padding: 16px;
}

/* Individual Option */
.option {
  display: flex;
  align-items: center;
  border: 2px solid #e5e7eb;
  padding: 12px;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
  background-color: white;
}
/* 
.option:hover {
  border-color: #71B3FFE5;
} */

/* Option content */
.option-content {
  flex-grow: 1;
  background-color: white;
}

/* Header section for the option */
.option-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 10px;
  border-radius: 10px;
  background-color: #EAFAF8;
}

/* Left-side: Keeps input and title in the same row */
.option-left {
  display: flex;
  align-items: center;
  gap: 10px;
}

/* Radio button */
.option-left input {
  width: 18px;
  height: 18px;
  cursor: pointer;
}

/* Title text */
.option-title {
  font-weight: bold;
  margin: 0;
}

/* Right-side: Price + "Per Person" text */
.option-right {
  text-align: right;
  margin-right: 50px;
}

/* Price styling */
.option-price {
  font-size: 20px;
  font-weight: bold;
  color: #2563eb;
  margin: 0;
}

/* "Per Person" text */
.persontext {
  font-size: 12px;
  color: #0c0d0d;
  font-weight: normal;
  display: block;
}

/* Option price for no thanks */
.option-price.gray {
  color: #6b7280;
}

/* Option List */
.option-list {
  font-size: 12px;
  color: #6b7280;
  padding: 15px 0;
  list-style-type: none;
}

/* Read More link */
.read-more {
  font-size: 14px;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-top: 1px solid #cacbce;
  border-bottom: 1px solid #cacbce;
  width: 100%;
  padding: 5px 0;
}

.read-more-icon {
  font-size: 20px;
  padding: 5px 30px;
  font-weight: bold;
}

/* Selected Option */
.selected {
  background-color: white !important;
}

/* Disclaimer */
.disclaimer {
  font-size: 16px;
  color: #6b7280;
  margin-top: 15px;
}



/* Responsive Design */
@media (max-width: 768px) {
  .card {
    width: 100%;
  }

  .header {
    flex-direction: row;
    align-items: center;
    text-align: center;
  }

  .header-left {
    align-items: center;
  }

  .icon {
    width: 80px;
    height: 60px;
  }

  .option-header {
    flex-direction: row;
    align-items: flex-start;
  }

  .option-right {
    text-align: left;
    padding-top: 5px;
  }
}




/* Responsive Design */
@media (max-width: 480px) {
  .card {
    width: 100%;
    
  }

  .header {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .header-left {
    align-items: center;
  }

  .icon {
    width: 80px;
    height: 60px;
  }

  .option-header {
    flex-direction: column;
    align-items: flex-start;
  }

  .option-right {
    text-align: left;
    padding-top: 5px;
  }
}
</style>
