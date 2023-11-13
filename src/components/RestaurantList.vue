<template>
    <div>
    <header class="page-header bg-success text-white text-center p-4">
      <h1>Search your restaurants</h1>
    </header>
    <div class="container mt-4">
      <div class="row justify-content-center">
        <div class="col-md-8">
          <div class="input-group mb-3">
            <input
              v-model="keyword"
              @input="searchRestaurants"
              placeholder="Enter restaurant name"
              class="form-control search-input"
            />
            <div class="input-group-append">
              <button @click="clearInput" class="btn btn-outline-secondary" type="button">Clear</button>
            </div>
          </div>
          <ul class="list-group restaurant-list">
            <li
              v-for="restaurant in restaurants"
              :key="restaurant.id"
              class="list-group-item restaurant-item"
            >
              {{ restaurant.name }} - {{ restaurant.formatted_address }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
  
<script>
import axios from 'axios';

export default {
    data() {
        return {
            keyword: 'Bang sue',
            restaurants: [],
        };
    },
    mounted() {
        this.searchRestaurants();
    },
    methods: {
        searchRestaurants() {
            // Use Axios to communicate with the Laravel API endpoint from env file
            axios.post(`${import.meta.env.VITE_API_ENDPOINT}/api/restaurant-laravel-test/search`, {
                query: this.keyword,
            }).then(response => {
                if (response.data.success) {
                    this.restaurants = response.data.data;
                }
            });
        },
        clearInput() {
            this.keyword = "";
        },
    },
};
</script>  

<style scoped>

</style>