<template>
  <div class="contact-container">
    <h1>Contact Us</h1>
    <form @submit.prevent="submitForm" class="contact-form">
      <label>
        Name:
        <input type="text" v-model="form.name" required />
      </label>

      <label>
        Email:
        <input type="email" v-model="form.email" required />
      </label>

      <label>
        Subject:
        <input type="text" v-model="form.subject" required />
      </label>

      <label>
        Message:
        <textarea v-model="form.message" required></textarea>
      </label>

      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'ContactPage',
  data() {
    return {
      form: {
        name: '',
        email: '',
        subject: '',
        message: ''
      }
    };
  },
  methods: {
    submitForm() {
      alert("Thank you for contacting us!");
      this.form = { name: '', email: '', subject: '', message: '' };
    }
  }
};
</script>

<style scoped>
.contact-container {
  max-width: 600px;
  margin: 50px auto;
  padding: 30px;
  background: #ffffff;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.contact-container h1 {
  text-align: center;
  margin-bottom: 30px;
  color: #333;
}

.contact-form label {
  display: block;
  margin-bottom: 15px;
  color: #555;
  font-weight: 500;
}

.contact-form input,
.contact-form textarea {
  width: 100%;
  padding: 10px 12px;
  margin-top: 5px;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 16px;
  transition: border-color 0.3s;
}

.contact-form input:focus,
.contact-form textarea:focus {
  border-color: #4caf50;
  outline: none;
}

.contact-form textarea {
  min-height: 100px;
  resize: vertical;
}

.contact-form button {
  display: block;
  margin: 20px auto 0;
  padding: 12px 30px;
  background-color: #4caf50;
  color: white;
  font-size: 16px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.contact-form button:hover {
  background-color: #45a049;
}


@media (max-width: 640px) {
  .contact-container {
    margin: 20px;
    padding: 20px;
  }

  .contact-form button {
    width: 100%;
  }
}
</style>
