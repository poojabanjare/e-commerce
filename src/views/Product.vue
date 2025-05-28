<template>
  <div class="product-page">
    <h2 class="product-heading fade-in">Our Products</h2>
    
    <div class="product-grid">
      <div
        v-for="(product, index) in products"
        :key="index"
        class="product-card fade-in"
      >
        <img :src="product.image" :alt="product.name" class="product-image" />
        <h3>{{ product.name }}</h3>
        <p>Price: ₹{{ product.price }}</p>

        <router-link :to="'/order/' + product.name">
          <button @click="goToOrder(product)" class="buy-button">
            Buy Now
          </button>
        </router-link>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "ProductPage",
  data() {
    return {
      products: [
        { name: "Laptop", price: 50000, image: "https://images.unsplash.com/photo-1717435970624-be6590120434?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" },
        { name: "Smartphone", price: 20000, image: "https://images.unsplash.com/photo-1709652880879-3b8e144eafe2?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" },
        { name: "Headphones", price: 1500, image: "https://images.unsplash.com/photo-1706290047883-64294c7e11c3?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3Dtext=Headphones" },
        { name: "Tablet", price: 18000, image: "https://media.istockphoto.com/id/520843471/photo/what-is-our-stock-doing-today.webp?a=1&b=1&s=612x612&w=0&k=20&c=qIWymWphQ3qRI9BzLwO0PH9Na2DiR0GnwfqEgGxpVfU=" },
        { name: "Keyboard", price: 800, image: "https://images.unsplash.com/photo-1584727151652-d09b17ebf23f?q=80&w=2111&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3Dtext=Keyboard" },
        { name: "Mouse", price: 500, image: "https://images.unsplash.com/photo-1660491083562-d91a64d6ea9c?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8V2lyZWxlc3MlMjBtb3VzZSUyMG9yJTIwZ2FtaW5nJTIwbW91c2V8ZW58MHx8MHx8fDA%3Dtext=Mouse" },
        { name: "Monitor", price: 7000, image: "https://images.unsplash.com/photo-1623278101003-eca0f433641c?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8N3x8RGVza3RvcCUyMG1vbml0b3IlMjBzaG93aW5nJTIwZGlzcGxheXxlbnwwfHwwfHx8MA%3D%3Dtext=Monitor" },
        { name: "Speaker", price: 2500, image: "https://plus.unsplash.com/premium_photo-1726769123522-81fb47e9758d?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTN8fEJsdWV0b290aCUyMHNwZWFrZXIlMjBvciUyMHN0ZXJlbyUyMHNldHxlbnwwfHwwfHx8MA%3D%3Dtext=Speaker" },
        { name: "Camera", price: 30000, image: "https://images.unsplash.com/photo-1616423640778-28d1b53229bd?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTh8fERTTFIlMjBvciUyMG1pcnJvcmxlc3MlMjBjYW1lcmF8ZW58MHx8MHx8fDA%3Dtext=Camera" },
        { name: "Printer", price: 6000, image: "https://images.unsplash.com/photo-1630327722923-5ebd594ddda9?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3Dtext=Printer" },
        { name: "Charger", price: 400, image: "https://images.unsplash.com/photo-1706290134049-c5c72d24146a?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3Dtext=Charger" },
        { name: "Power Bank", price: 1200, image: "https://media.istockphoto.com/id/1830428413/photo/two-9v-batteries.webp?a=1&s=612x612&w=0&k=20&c=47ExZRVhIHt5AtxBWagPO3LgjokYYkb50A3cPuKsD98=text=PowerBank" },
        { name: "Webcam", price: 1800, image: "https://images.unsplash.com/photo-1623949556303-b0d17d198863?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8VVNCJTIwd2ViY2FtJTIwb3IlMjBsYXB0b3AlMjB3ZWJjYW18ZW58MHx8MHx8fDA%3Dtext=Webcam" },
        { name: "Router", price: 1500, image: "https://plus.unsplash.com/premium_photo-1671017801457-5d8e846d16b6?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTd8fFdpJTIwRmklMjByb3V0ZXIlMjB3aXRoJTIwYW50ZW5uYXN8ZW58MHx8MHx8fDA%3Dtext=Router" },
        { name: "Pen Drive", price: 600, image: "https://media.istockphoto.com/id/476801528/photo/black-foading-thumb-drive-with-clipping-path.webp?a=1&b=1&s=612x612&w=0&k=20&c=B7XzSm7xt_wcYR2b7F1WrX8hQKF7RQ44rr7Tv0xjDt0=text=Pendrive" },
        { name: "External HDD", price: 4000, image: "https://images.unsplash.com/photo-1611887052633-33a0d81924b3?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTR8fFBvcnRhYmxlJTIwaGFyZCUyMGRyaXZlJTIwYmVzaWRlJTIwYSUyMGxhcHRvcHxlbnwwfHwwfHx8MA%3D%3Dtext=HDD" },
        { name: "SSD", price: 3500, image: "https://media.istockphoto.com/id/621977854/photo/hard-disks-and-solid-state-sata-drives.jpg?s=2048x2048&w=is&k=20&c=PsP24Yu7f5PlpDEh0s_34NuFJ45g90k1lVmL99na7Q4=text=SSD" },
        { name: "Microphone", price: 900, image: "https://plus.unsplash.com/premium_photo-1664195074777-a7c40926f5c2?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NXx8U3R1ZGlvJTIwbWljJTIwb3IlMjBwb2RjYXN0JTIwbWljJTIwc2V0dXB8ZW58MHx8MHx8fDA%3Dtext=Mic" },
        { name: "Tripod", price: 1100, image: "https://images.unsplash.com/photo-1571253066662-32bf8be4135b?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8OHx8Q2FtZXJhJTIwdHJpcG9kJTIwb3IlMjBtb2JpbGUlMjB0cmlwb2R8ZW58MHx8MHx8fDA%3Dtext=Tripod" },
        { name: "Smartwatch", price: 7000, image: "https://images.unsplash.com/photo-1620618802705-79f663a9012a?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8N3x8c21hcnQlMjB3YXRjaCUyMHNob3dpbmclMjBkaXNwbGF5fGVufDB8fDB8fHwwtext=Smartwatch" },
        { name: "Fitness Band", price: 2000, image: "https://images.unsplash.com/photo-1676173647178-e8bfdc144d76?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3Dtext=FitnessBand" },
        { name: "Bluetooth Earbuds", price: 2500, image: "https://images.unsplash.com/photo-1739764574641-45dbb094a3f0?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Nnx8V2lyZWxlc3MlMjBlYXJidWRzJTIwaW4lMjBjaGFyZ2luZyUyMGNhc2V8ZW58MHx8MHx8fDA%3Dtext=Earbuds" },
        { name: "Projector", price: 25000, image: "https://plus.unsplash.com/premium_photo-1748188813889-bfc17accb2f2?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MXx8UHJvamVjdG9yJTIwd2l0aCUyMHNjcmVlbiUyMHByb2plY3Rpb258ZW58MHx8MHx8fDA%3Dtext=Projector" },
        { name: "Gamepad", price: 1500, image: "https://images.unsplash.com/photo-1654484520941-ebbba5b77fec?q=80&w=2074&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3Dtext=Gamepad" },
        { name: "VR Headset", price: 40000, image: "https://plus.unsplash.com/premium_photo-1710962439403-a35fbc684b15?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MzN8fEhlYWRzZXQlMjB3b3JuJTIwb3IlMjBvbiUyMGElMjB0YWJsZXxlbnwwfHwwfHx8MA%3D%3Dtext=VRHeadset" },
        { name: "Graphics Card", price: 35000, image: "https://images.unsplash.com/photo-1589580173879-46993181bae4?q=80&w=1884&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3Dtext=GPU" },
        { name: "TV", price: 30000, image: "https://plus.unsplash.com/premium_photo-1681044639299-3d461cbb9f8b?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8OXx8TEVEJTIwVFYlMjBvbiUyMHdhbGwlMjBvciUyMHN0YW5kfGVufDB8fDB8fHwwtext=TV" },
        { name: "Air Conditioner", price: 35000, image: "https://plus.unsplash.com/premium_photo-1679943423706-570c6462f9a4?q=80&w=1905&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3Dtext=AC" },
        { name: "Refrigerator", price: 25000, image: "https://images.unsplash.com/photo-1722603929403-de9e80c46a9a?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTB8fEZyaWRnZSUyMHdpdGglMjBvcGVuJTIwZG9vcnxlbnwwfHwwfHx8MA%3D%3Dtext=Fridge" },
        { name: "Washing Machine", price: 22000, image: "https://images.unsplash.com/photo-1626806819282-2c1dc01a5e0c?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8d2FzaGluZyUyMG1hY2hpbmV8ZW58MHx8MHx8fDA%3Dtext=Washer" }
      ]
    };
    
  },
  methods: {
  goToOrder(product) {
    this.$router.push({ name: 'OrderPage', params: { name: product.name } });
  }
}

  
};
</script>

<style scoped>
.product-page {
  padding: 20px;
  text-align: center;
}

.product-heading {
  font-size: 2rem;
  margin-bottom: 30px;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
}

.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
}

.product-card {
  background: #ffffff;
  border-radius: 12px;
  padding: 20px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.product-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}

.product-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 8px;
}

.buy-button {
  background-color: #008080;
  color: white;
  padding: 8px 14px;
  margin-top: 10px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.buy-button:hover {
  background-color: #005f5f;
}

.fade-in {
  animation: fadeIn 1s ease-in-out;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
    transform: translateY(10px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

</style>
