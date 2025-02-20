<template>
<div class="container">
    <!-- Main Heading outside the Card, Left Aligned -->
    <h2 class="main-heading">
        <i class="fa fa-suitcase-rolling heading-icon"></i>
        Lost Baggage Protection
    </h2>

    <div class="card">
        <!-- Blue box at the top of the card -->
        <div class="blue-box">
            <div class="recommended-heading">Recommended</div>
            <!-- New heading below recommended heading -->
            <div class="protection-heading">Baggage Protection</div>
            <img src="../assets/images/bagg.jpg" alt="Baggage Protection" class="blue-box-image" />
        </div>

        <p class="bordered">Did you know: 20 million bags are mishandled by airlines every year!</p>

        <div class="options">

            <!-- Lost Baggage Protection Option -->
            <label class="option" :class="{ 'selected': selectedSupport === 'premium' }">
                <div class="option-content">
                    <div class="option-header">
                        <!-- Left side: Radio button and title in one row -->
                        <label class="option-left">
                            <input type="radio" name="baggage" :checked="baggageProtection" @change="updateBaggageSelection(true)" />
                            <p class="option-title">&nbsp;&nbsp;Yes, I want to protect my baggage</p>
                        </label>
                        <!-- Right side: Price and "Per Person" text -->
                        <div class="option-right">
                            <p class="option-price">$15</p>
                            <span class="persontext">Per Person</span>
                        </div>
                    </div>

                    <ul class="option-list">
                        <li>✔ Receive real-time push notifications via email & SMS regarding the status of your delayed baggage</li>
                        <li>✔ Collect $1,000 per bag that is not returned within 96 hours</li>
                        <li>✔ No proof of contents or receipts are required in order to receive payment</li>
                    </ul>

                </div>
            </label>

            <!-- No Thanks Option -->
            <label class="option" :class="{ 'selected': selectedSupport === 'none' }">
                <div class="option-content">
                    <div class="option-header">
                        <!-- Left side: Radio button and title in one row -->
                        <label class="option-left">
                            <input type="radio" name="baggage" :checked="!baggageProtection" @change="updateBaggageSelection(false)" />
                            <p class="option-title">No, I’m willing to risk losing my baggage</p>
                        </label>
                        <!-- Right side: Price and "Per Person" text -->
                        <div class="option-right">
                            <p class="option-price">$0.00</p>
                        </div>
                    </div>
                </div>
            </label>
        </div>
        <p class="terms">By adding baggage protection, you agree to the <a href="#">Blue Ribbon Bags Terms & Conditions</a>.</p>
    </div>

    <h2 class="main-heading">
        <i class="fa fa-calendar-check heading-icon"></i>
        Extended Cancellation Policy
    </h2>
    <div class="card">
        <div class="blue-box background-color">
            <div class="recommended-heading">Recommended</div>
            <!-- New heading below recommended heading -->
            <div class="protection-heading">Cancellation protection </div>
            <img src="../assets/images/a man.jpg" alt="Baggage Protection" class="blue-box-image" />
        </div>

        <p class="bordered">Choose cancellation protection and receive a total refund of $181.83!</p>

        <div class="options">

            <!-- Premium Support Option -->
            <label class="option" :class="{ 'selected': selectedSupport === 'premium' }">
                <div class="option-content">
                    <div class="option-header">
                        <!-- Left side: Radio button and title in one row -->
                        <label class="option-left">
                            <input type="radio" name="cancellation" :checked="cancellationProtection" @change="updateCancellationSelection(true)" />
                            <p class="option-title">Yes, I want cancellation protection</p>
                        </label>
                        <!-- Right side: Price and "Per Person" text -->
                        <div class="option-right">
                            <p class="option-price">$15</p>
                            <span class="persontext">Per Person</span>
                        </div>
                    </div>

                    <ul class="option-list">
                        <li>✔Cancel or Re-book Your Booking For Any Reason Within 24 Hours</li>
                        <li>✔ If you wish to cancel, kindly email us at support@flightschannel.com</li>

                    </ul>

                </div>
            </label>

            <!-- No Thanks Option -->
            <label class="option" :class="{ 'selected': selectedSupport === 'none' }">
                <div class="option-content">
                    <div class="option-header">
                        <!-- Left side: Radio button and title in one row -->
                        <label class="option-left">
                            <input type="radio" name="cancellation" :checked="!cancellationProtection" @change="updateCancellationSelection(false)" />
                            <p class="option-title">No thanks</p>
                        </label>
                        <!-- Right side: Price and "Per Person" text -->
                        <div class="option-right">
                            <p class="option-price">$0.00</p>
                        </div>
                    </div>
                </div>
            </label>

        </div>
        <p class="terms"> * Extended Cancellation Policy Is Non- Refundable Once Purchased.</p>
    </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      baggageProtection: false, // Default: No baggage protection
      cancellationProtection: false, // Default: No cancellation protection
    };
  },
  methods: {
    updateBaggageSelection(value) {
      this.baggageProtection = value;
      this.$emit("update-baggage", value); // Emit value to parent
    },
    updateCancellationSelection(value) {
      this.cancellationProtection = value;
      this.$emit("update-cancellation", value); // Emit value to parent
    }
  }
};
</script>


<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    color: #333;
    padding: 20px;

}

.container {
    max-width: 100%;
    padding: 20px;
    background-color: #EAF3F2;
}

.main-heading {
    font-size: 1.5em;
    font-weight: bold;
    margin-bottom: 10px;
    text-align: left;
    color: black;
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 10px 10px;
}

.heading-icon {
    font-size: 1.2em;
    color: black;
}

.card {
    background: #fff;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    margin-bottom: 20px;
    overflow: hidden;
    padding: 20px;
}

.bordered {
    border: 2px solid #EAFAF8;
    border-radius: 5px;
    padding: 10px;
    margin-bottom: 10px;
    background-color: #EAFAF8;
}

.blue-box {
    background-color: #71B3FF;
    height: 150px;
    width: 100%;
    margin-bottom: 10px;
    position: relative;
    border-radius: 5px 5px 0px 0px;
}

.recommended-heading {
    position: absolute;
    top: 30px;
    left: 80px;
    background-color: #4ACFFF;
    color: white;
    padding: 5px 10px;
    border-radius: 5px;
    border: 2px solid #4ACFFF;
}

/* New style for protection heading */
.protection-heading {
    position: absolute;
    top: 70px;
    left: 50px;
    font-size: 1.2em;
    font-weight: bold;
    color: white;
    padding: 5px 10px;
}

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

/* Option content */
.option-content {
    flex-grow: 1;
    background-color: white;
}

/* Header section for the option */
.option-header {
    display: flex;
    justify-content: left;
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
    width: 50%;
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
    width: 50%;
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

/* Disclaimer */
.disclaimer {
    font-size: 16px;
    color: #6b7280;
    margin-top: 15px;
}

.background-color {
    background-color: #4B4DC8;
}

.blue-box-image {
    max-width: 200px;
    height: auto;
    position: absolute;
    right: 20px;
    top: 50%;
    transform: translateY(-50%);
    border-radius: 10px;
}

.terms a {
    color: #007bff;
    text-decoration: none;
}

.terms a:hover {
    text-decoration: underline;
}

@media (max-width: 768px) {
    .recommended-heading {
        left: 60px;
        top: 20px;
    }

    .protection-heading {
        top: 70px;
        left: 2rem;
    }

    .main-heading {
        font-size: 1.2em;
    }

    .blue-box {
        height: 120px;
    }

    .blue-box-image {
        max-width: 150px;
        right: 15px;
    }
}

@media (max-width: 480px) {

    .main-heading {
        font-size: 18px;
    }

    .recommended-heading {
        left: 20px;
        top: 15px;
        width: 100px;
        font-size: 10px;
    }

    .protection-heading {
        top: 50px;
        font-size: 12px;
        left: 3px;
    }

    .blue-box {
        height: 100px;
    }

    .blue-box-image {
        max-width: 80px;
        right: 10px;
    }

    .bordered {
        font-size: 12px;
    }

    .option-box .content .description {
        font-size: 12px;
    }

    .terms {
        font-size: 12px;
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
