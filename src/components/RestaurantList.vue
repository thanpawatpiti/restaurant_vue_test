<template>
    <div class="search-container">
        <input v-model="keyword" @input="searchRestaurants" placeholder="Enter keyword" class="search-input">
        <ul class="restaurant-list">
            <li v-for="restaurant in restaurants" :key="restaurant.id" class="restaurant-item">
                {{ restaurant.name }} - {{ restaurant.formatted_address }}
            </li>
        </ul>
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
            axios.post(`http://127.0.0.1:8000/api/restaurant-laravel-test/search`, {
                query: this.keyword,
            }).then(response => {
                console.log(response.data);
                // console.log(`${process.env.VUE_APP_API_ENDPOINT}`);
                if (response.data.success) {
                    this.restaurants = response.data.data;
                }
            });
        },
    },
};
</script>  

<style scoped>
.search-container {
    max-width: 400px;
    margin: auto;
    text-align: center;
}

.search-input {
    padding: 10px;
    font-size: 16px;
    width: 100%;
    box-sizing: border-box;
    margin-bottom: 10px;
}

.restaurant-list {
    list-style-type: none;
    padding: 0;
}

.restaurant-item {
    background-color: #f8f8f8;
    border: 1px solid #ddd;
    padding: 10px;
    margin-bottom: 5px;
    border-radius: 5px;
}
</style>