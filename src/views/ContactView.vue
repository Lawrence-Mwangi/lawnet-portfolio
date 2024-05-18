<script setup>
import { ref } from 'vue';
import Emailjs from 'emailjs-com';

const serviceId = import.meta.env.VITE_EMAILJS_SERVICE_ID;
const templateId = import.meta.env.VITE_EMAILJS_TEMPLATE_ID;
const userId = import.meta.env.VITE_EMAILJS_USER_ID;

const first_name = ref('');
const last_name = ref('');
const email = ref('');
const message = ref('');

const emailSent = ref(false);
const errorMessage = ref('');
const successMessage = ref('');
const clearFormAndMessage = () => {
  [first_name, last_name, email, message].forEach((ref) => (ref.value = ''));

  // Delay clearing the form and success message for a few seconds
  setTimeout(() => {
    successMessage.value = '';
    emailSent.value = false;
  }, 3000); 
};

const showMessage = (messageRef, duration) => {
  setTimeout(() => (messageRef.value = ''), duration);
};

const sendEmail = async () => {
  const templateParams = {
    from_first_name: first_name.value,
    from_last_name: last_name.value,
    from_email: email.value,
    message: message.value,
  };

  try {
    const response = await Emailjs.send(serviceId, templateId, templateParams, userId);
    emailSent.value = true;
    successMessage.value = 'Email sent successfully!';
    showMessage(successMessage, 3000);

    setTimeout(clearFormAndMessage, 3000);
  } catch (error) {
    console.error('Email sending failed:', error);
    errorMessage.value = 'Email sending failed. Please try again.';
    showMessage(errorMessage, 3000);
  }
};

Emailjs.init(userId);
</script>

<template>
    <div class="contact_container">
        <h1 class="title"><span class="brackets">&lt; Contact us &gt;</span></h1>
        <div class="contact_content">
            <div class="contact_infor">
                <p><span class="icon"><img src="../assets/images/gmail.png" alt="gmail icon" width="25px" height="25px"></span> mwangilawrence661@gmail.com</p>
                <p><span class="icon"><img src="../assets/images/phone.png" alt="gmail icon" width="25px" height="25px"></span>+254 799 509 242</p>
            </div>
            <div class="contact_form">
              <div v-if="emailSent && successMessage" class="success-message">{{ successMessage }}</div>
                <p v-if="errorMessage" class="error-message">{{ errorMessage }}</p>
                <form @submit.prevent="sendEmail">
                    <div class="input_group">
                        <div class="name">
                            <input type="text" name="first_name" id="first_name" v-model="first_name" placeholder="Enter first name" required>
                            <input type="text" name="last_name" id="last_name" v-model="last_name" placeholder="Enter last name" required>
                        </div>
                        <div class="input_group">
                            <input type="email" name="email" id="email"  v-model="email" placeholder="Enter you email" required>
                        </div>
                        <div class="input_group">
                            <textarea name="message" id="message" cols="7" rows="5" v-model="message" placeholder="Type you message here" required></textarea>
                        </div>
                    </div>
                    <button type="submit">Submit</button>
                </form>
            </div>
        </div>
    </div>
</template>