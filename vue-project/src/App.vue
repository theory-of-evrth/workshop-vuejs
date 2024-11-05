<script >
import { computed } from 'vue';

export default {
  // Properties returned from data() become reactive state
  // and will be exposed on `this`.
  data() {

    return {
      count: 0,
      selectedImage: 0,
      logo: "/logo.svg",

      coffees: [
      {
    id: 1,
    name: 'Some weird coffee',
    price: 2,
    stock: 3,
  },
  {
    id: 2,
    name: 'Espresso',
    price: 5,
    stock: 1,
  },
  {
    id: 3,
    name: 'Evil coffee',
    price: 389427,
    stock: 4,
  },
  {
    id: 4,
    name: 'Latte',
    price: 10,
    stock: 5,
  }
      ],
      carouselImages: [
  {
    id: 1,
    text: 'Capsule 1',
    image: '/assets/images/colombia.png',
  },
  {
    id:  2,
    text: 'Capsule 2',
    image: './assets/images/colombia_de_cote.png',
  },
  {
    id: 3,
    text: 'Tasse',
    image: './assets/images/colombia_tasse.png',
  },
  {
    id: 4,
    text: 'Paquet',
    image: './assets/images/colombia_paquet.png',
  }
],
    }
  },

  // Methods are functions that mutate state and trigger updates.
  // They can be bound as event handlers in templates.
  methods: {
    increment() {
      this.count++
    },

    order()
    {
      this.coffees[this.selectedImage].stock--
    },


    updateSelectedImage(index) { this.selectedImage = index },

    image() { return this.carouselImages[this.selectedImage].image }
  },

  computed: {
  title() {
    return `Order ${this.coffees[this.selectedImage]?.name || 'Coffee'}`;
  },
}
}

</script>

<template>
  <header>
    <img alt="Vue logo" :class="[coffees[selectedImage].stock < 20 ? 'logo' : 'hidden']" v-on:click="coffees[selectedImage].stock += 1" v-bind:src="logo" width="125" height="125" />

  </header>

  <main>
  <h1>{{title}}</h1>
  <p>click count button to augment count, click the big logo to decrement</p>
  <button  @click="order" :disabled="coffees[selectedImage].stock <= 0">Count is: {{ coffees[selectedImage].stock }} <img alt="Vue logo" class="logo" v-bind:src="logo" width="20" height="20" /></button>
  <p v-if="coffees[selectedImage].stock%2==0">even count</p>
  <p v-else>odd count</p>
  <p v-show="coffees[selectedImage].stock > 10 && coffees[selectedImage].stock < 20">You clicked a lot!</p>
  <p v-if="coffees[selectedImage].stock==20">You are clicking too wildly, we have to disable count. <br>You won't really drink that much</p>

  <p>You selected<img height="30" alt="selected coffee" :src="image()"></p>

  <h2>We sell:</h2>
  <ul>
  <li v-for="coffee in coffees" :key="coffee.id">
    {{ coffee.name }}, {{ coffee.price }}$
  </li>
  </ul>

  <div>
  <span
    v-for="carouselImage in carouselImages"
    :key="carouselImage.id"
    @click="updateSelectedImage(carouselImage.id-1)"
  >
    <img height="50" alt="carouselImage.text" :src="carouselImage.image" />
  </span>
</div>

  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}

.hidden {
  display:none
}

</style>
