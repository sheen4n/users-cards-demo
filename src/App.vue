<template>
  <div class="bg-red-400 h-full p-10 flex flex-col">
    <h1 class="font-bold mx-auto inline-block text-2xl">Users List</h1>
    <p class="mx-auto mt-8" v-if="isLoading">Loading Data...</p>
    <p class="mx-auto mt-8" v-else>Showing {{ usersCount }} users</p>
    <div class="mt-8 flex flex-wrap justify-center">
      <UserCard v-for="user in usersData" :key="user.id" :user="user" />
    </div>
  </div>
</template>

<script>
import UserCard from './components/UserCard.vue';
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      usersData: [],
      isLoading: false,
    };
  },
  components: {
    UserCard,
  },
  computed: {
    usersCount() {
      return this.usersData.length;
    },
  },
  methods: {
    async loadData() {
      this.isLoading = true;
      try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/users');
        this.usersData = response.data;
      } catch (error) {
        console.log(error);
      } finally {
        this.isLoading = false;
      }
    },
  },
  mounted() {
    this.loadData();
  },
};
</script>

<style>
html,
body {
  height: 100%;
}
</style>
