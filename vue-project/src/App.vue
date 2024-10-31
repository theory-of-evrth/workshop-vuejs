<script >
export default {
  // Properties returned from data() become reactive state
  // and will be exposed on `this`.
  data() {
    return {
      count: 0,
      logo: "/logo.svg",
      title: "Order Nespresso",
      coffees: [
      {
    id: 1,
    name: 'Some weird coffee',
    price: 2,
  },
  {
    id: 2,
    name: 'Espresso',
    price: 5,
  },
  {
    id: 3,
    name: 'Evil coffee',
    price: 389427,
  },
  {
    id: 4,
    name: 'Latte',
    price: 10,
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
    }
  }
}

</script>

<template>
  <header>
    <img alt="Vue logo" :class="[count > 0 ? 'logo' : 'hidden']" v-on:click="count -= 1" v-bind:src="logo" width="125" height="125" />

  </header>

  <main>
  <h1>{{title}}</h1>
  <p>click count button to augment count, click the big logo to decrement</p>
  <button @click="increment">Count is: {{ count }} <img alt="Vue logo" class="logo" v-bind:src="logo" width="20" height="20" /></button>
  <p v-if="count%2==0">even count</p>
  <p v-else>odd count</p>
  <p v-show="count > 10 && count < 20">You clicked a lot!</p>

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
    @mouseover="updateImage(carouselImage.image)"
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
