<template>
  <div class="container py-5">
    <!-- use NavTabs -->
    <NavTabs />
    <h1 class="mt-5">人氣餐廳</h1>
    <hr />
    <RestaurantsTopContent
      v-for="restaurant in restaurants"
      :key="restaurant.id"
      :initial-restaurant="restaurant"
    />
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";
import RestaurantsTopContent from "../components/RestaurantsTopContent";
import restaurantsAPI from "../apis/restaurants";
import { Toast } from "../utils/helpers";

export default {
  components: {
    NavTabs,
    RestaurantsTopContent
  },
  data() {
    return {
      restaurants: []
    };
  },
  created() {
    this.fetchRestaurants();
  },
  methods: {
    async fetchRestaurants() {
      try {
        const { data } = await restaurantsAPI.getRestaurantsTop();
        const { restaurants } = data;
        this.restaurants = restaurants;

        console.log(this.restaurants);
      } catch (error) {
        Toast.fire({
          icon: "error",
          title: "伺服器忙碌中，請稍後再試"
        });
        console.log("err", error);
      }
    }
  }
};
</script>