<script >
export default {
  // Properties returned from data() become reactive state
  // and will be exposed on `this`.
  data() {
    return {
      count: 0,
      logo: "/logo.svg",
      title: "Order Nespresso"
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
    <img alt="Vue logo" class="logo" v-bind:src="logo" width="125" height="125" />

  </header>

  <main>
  <h1>{{title}}</h1>
  <button @click="increment">Count is: {{ count }} <img alt="Vue logo" class="logo" v-bind:src="logo" width="20" height="20" /></button>
  <p v-if="count%2==0">even count</p>
  <p v-else>odd count</p>
  <p v-show="count > 10 && count < 20">You clicked a lot!</p>
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
</style>
