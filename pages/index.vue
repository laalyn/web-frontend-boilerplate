<template>
  <div>
    <!-- use a component -->
    <Logo />
    <!-- use <form> to get autocomplete, -->
    <!-- but don't use form submit button -->
    <form>
      <input v-model="form.first_name" placeholder="First name" type="text">
      <input v-model="form.last_name" placeholder="Last name" type="text">
    </form>
    <!-- use a function on @click or v-on:click (same thing) -->
    <!-- tailwindcss uses classes -->
    <button class="bg-green-300" @click="submitForm">Submit</button>
    <!-- use a variable -->
    <h1 class="inline-block">{{ form.first_name }}</h1>
    <h1 class="inline-block">{{ form.last_name }}</h1>
    <h1>{{ demo }}</h1>
  </div>
</template>

<!-- JavaScript reccommended -->
<script lang="js">
// import stuff here
import { axios } from 'axios'; // makes http requests

// real stuff here
export default {
  // variables go here, must be a function that returns stuff
  data() {
    return {
      form: {
        first_name: '',
        last_name: '',
      },
      demo: 'this is from a variable',
    };
  },
  // hooks
  async beforeCreate() {
    console.log('before create');
  },
  async created() {
    console.log('created');
  },
  async beforeMount() {
    console.log('before mount');
  },
  async mounted() {
    console.log('mounted');
  },
  // functions go here
  methods: {
    async submitForm() {
      try {
        let result = await this.$axios.get('http://localhost:3333/demo');
        console.log(result);
      } catch (error) {
        console.log(error);
      }
    }
  }
}
</script>
