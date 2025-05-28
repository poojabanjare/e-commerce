<template>
  <div>
  
    <section class="banner">
      <img
        class="banner-image"
        src="https://images.unsplash.com/photo-1590483200604-e9e60b6cb2dc?w=1080"
        alt="Welcome Banner"
      />
      <div class="banner-text">
        <h1>Welcome to Our Shop</h1>
        <p>Explore top products at best prices</p>
      </div>
    </section>

   
    <section class="about">
      <h2>About Us</h2>
      <p>
        We are passionate about providing the best tech products at unbeatable prices.
        Our goal is to make shopping easy and enjoyable for everyone.
      </p>
    </section>

  
    <section class="contact">
      <h2>Contact Us</h2>
      <p>Email: contact@ecommercestore.com</p>
      <p>Phone: +91 9876543210</p>
    </section>
  </div>
</template>

<script>
export default {
  name: 'HomePage'
};
</script>

<style scoped>

body {
  margin: 0;
  font-family: 'Segoe UI', sans-serif;
}


.banner {
  position: relative;
  width: 100%;
  height: 60vh;
  overflow: hidden;
}

.banner-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 2s ease;
}

.banner:hover .banner-image {
  transform: scale(1.05);
}

.banner-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.7);
  text-align: center;
  animation: fadeIn 2s ease-in-out;
}

.banner-text h1 {
  font-size: 3em;
  margin: 0;
}

.banner-text p {
  font-size: 1.2em;
  margin-top: 10px;
}


.about,
.contact {
  padding: 40px 20px;
  margin: 20px;
  background-color: #f0f4f8;
  color: #333;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.about:hover,
.contact:hover {
  transform: translateY(-5px);
}


@media (max-width: 768px) {
  .banner-text h1 {
    font-size: 2em;
  }

  .banner-text p {
    font-size: 1em;
  }

  .about, .contact {
    margin: 10px;
    padding: 30px 15px;
  }
}


@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translate(-50%, -60%);
  }
  to {
    opacity: 1;
    transform: translate(-50%, -50%);
  }
}
</style>
