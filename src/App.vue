<template>
  <div>
    <header>
      <div class="container">
        <h1>ZragCell</h1>
        <nav>
          <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#products">Products</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </nav>
      </div>
    </header>
    <div class="q-pa-md">
    <q-carousel
      animated
      v-model="slide"
      navigation
      infinite
      :autoplay="autoplay"
      arrows
      transition-prev="slide-right"
      transition-next="slide-left"
      @mouseenter="autoplay = false"
      @mouseleave="autoplay = true"
    >
      <q-carousel-slide :name="1" img-src="/images/bacground5.jpeg" />
      <q-carousel-slide :name="2" img-src="/images/bacground2.jpeg" />
      <q-carousel-slide :name="3" img-src="/images/bacground3.jpeg" />
      <q-carousel-slide :name="4" img-src="/images/ip16plus.jpeg" />
    </q-carousel>
  </div>

    <section id="home" class="hero">
      <div class="container">
        <h2>Welcome to ZragCell</h2>
        <p>Your premium destination for top-tier iPhones</p>
        <a href="#products" class="btn">Shop Now</a>
      </div>
    </section>

    <div class="q-pa-md row items-start q-gutter-md">
    <q-card class="my-card" flat bordered>
      <q-img
        src="/images/card.jpeg"
      />

      <q-card-section>        
        <div class="text-h5 q-mt-sm q-mb-xs">Zakia Aulia Putra</div>
        <div class="text-caption text-grey">
          Owner Of ZragCell
        </div>
      </q-card-section>

      <q-card-actions>
        <q-btn flat color="primary" label="Instagram" href="https://www.instagram.com/zakiaauliaputra?igsh=MXkyMW5iZG84dnk5Nw==" target="_blank"/>
        

        <q-space />

        <q-btn
          color="grey"
          round
          flat
          dense
          :icon="expanded ? 'keyboard_arrow_up' : 'keyboard_arrow_down'"
          @click="expanded = !expanded"
        />
      </q-card-actions>

      <q-slide-transition>
        <div v-show="expanded">
          <q-separator />
          <q-card-section class="text-subtitle2">
            {{ lorem }}
          </q-card-section>
        </div>
      </q-slide-transition>
    </q-card>
  </div>

    <section id="products" class="products">
      <div class="container">
        <h2>Featured Products</h2>
        <div class="product-grid">
          <div v-for="product in products" :key="product.id" class="product-card">
            <img :src="product.image" :alt="product.name" />
            <h3>{{ product.name }}</h3>
            <p>{{ product.price }}</p>
          </div>
        </div>
      </div>
    </section>

    <section id="about" class="about">
      <div class="container">
        <h2>About Us</h2>
        <p>At ZragCell,we offer an exclusive selection of premium quality iPhones. Our commitment is to bring you the best in quality and technology.


</p>
      </div>
    </section>

    <section id="contact" class="contact">
      <div class="container">
        <h2>Contact Us</h2>
        <form @submit.prevent="submitForm">
          <label for="name">Name:</label>
          <input type="text" id="name" v-model="form.name" required />
          
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="form.email" required />
          
          <label for="message">Message:</label>
          <textarea id="message" v-model="form.message" required></textarea>
          
          <button type="submit" class="btn">Submit</button>
        </form>
      </div>
    </section>
  </div> 
  <footer class="bg-body-tertiary text-center text-lg-start"> 
  <div class="text-center p-3" style="background-color: rgba(0, 0, 0, 0.05);">
    © 2024 Copyright
    <a class="text-body">Zakia Aulia Putra</a>
  </div>
  <!-- Copyright -->
</footer>  
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const slide = ref(1);
    const autoplay = ref(true);
    const products = ref([
      { id: 1, name: 'iPone15pro', price: 'Rp 26.699.000', image: '/images/iplipat.jpeg' },
      { id: 2, name: 'iPhone12', price: 'Rp 11.999.000', image: '/images/ip12.jpeg' },
      { id: 2, name: 'iPone13 Pro', price: 'Rp 15.499.000', image: '/images/ip13pro.jpeg' },
      { id: 2, name: 'iPhone15 pro', price: 'Rp 22.499.000', image: '/images/ip15plus.jpeg' },
      { id: 3, name: 'iPhone xr', price: 'Rp 9.499.000', image: '/images/ip10.jpeg' }
    ]);

    const form = ref({
      name: '',
      email: '',
      message: ''
    });

    const submitForm = () => {
      alert(`Name: ${form.value.name}\nEmail: ${form.value.email}\nMessage: ${form.value.message}`);
      form.value.name = '';
      form.value.email = '';
      form.value.message = '';
    };

    return {
      slide,
      autoplay,
      products,
      form,
      submitForm,
      expanded: ref(false),
      lorem: 'Zakia Aulia Putra, seorang PENGUSAHA muda yang masih berusia 20 tahun.'
    };
  }
}
</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  color: #333;
}

header {
  background-color: #3a1851;
  color: #fff;
  padding: 1em 0;
}

header .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1em;
}

header nav ul {
  list-style: none;
  display: flex;
  gap: 1em;
}

header nav a {
  color: #fff;
  text-decoration: none;
}

.hero {
  background: url('/images/shop1.jpeg') no-repeat center center/cover;
  color: #fff;
  text-align: center;
  padding: 5em 1em;
}

.products {
  padding: 2em 1em;
  background-color: #f9f9f9;
}

.product-grid {
  display: flex;
  gap: 1em;
  flex-wrap: wrap;
}

.product-card {
  background-color: #fff;
  border: 1px solid #ddd;
  padding: 1em;
  flex: 1 1 calc(33.333% - 2em);
  box-sizing: border-box;
  text-align: center;
}

.product-card img {
  max-width: 100%;
  height: auto;
}

.about, .contact {
  padding: 2em 1em;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1em;
}

.btn {
  background-color: #333;
  color: #fff;
  padding: 0.5em 1em;
  text-decoration: none;
  border-radius: 5px;
}

form label {
  display: block;
  margin: 0.5em 0 0.25em;
}

form input, form textarea {
  width: 100%;
  padding: 0.5em;
  margin-bottom: 1em;
  border: 1px solid #ddd;
  border-radius: 5px;
}

form button {
  background-color: #333;
  color: #fff;
  padding: 0.5em 1em;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
</style>
