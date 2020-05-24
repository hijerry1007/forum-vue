<template>
  <div class="card mb-3" style="max-width: 540px;margin: auto;">
    <div class="row no-gutters">
      <div class="col-md-4">
        <router-link :to="{name: 'restaurant', params: {id: restaurant.id}}">
          <img class="card-img" :src="restaurant.image" />
        </router-link>
      </div>
      <div class="col-md-8">
        <div class="card-body">
          <h5 class="card-title">{{restaurant.name}}</h5>
          <span class="badge badge-secondary">收藏數：{{restaurant.FavoriteCount}}</span>
          <p class="card-text">{{restaurant.description}}</p>
          <router-link
            :to="{name: 'restaurant', params: {id: restaurant.id}}"
            class="btn btn-primary mr-2"
          >Show</router-link>

          <button
            v-if="restaurant.isFavorited"
            type="button"
            class="btn btn-danger mr-2"
            @click.stop.prevent="deleteFavorite(restaurantId)"
          >移除最愛</button>
          <button
            v-else
            type="button"
            class="btn btn-primary"
            @click.stop.prevent="addFavorite(restaurantId)"
          >加到最愛</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import usersAPI from "../apis/users";
import { Toast } from "../utils/helpers";
export default {
  props: {
    initialRestaurant: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      restaurant: this.initialRestaurant
    };
  },
  methods: {
    async addFavorite(restaurantId) {
      try {
        const { data } = await usersAPI.addFavorite({ restaurantId });
        console.log("data", data);

        this.restaurant = {
          ...this.restaurant,
          isFavorited: true,
          FavoriteCount: this.restaurant.FavoriteCount + 1
        };
      } catch (error) {
        Toast.fire({
          icon: "error",
          title: "無法追蹤餐廳，請稍後再試"
        });
        console.log("error", error);
      }
    },
    async deleteFavorite(restaurantId) {
      try {
        const { data } = await usersAPI.deleteFavorite({ restaurantId });
        console.log("data", data);

        this.restaurant = {
          ...this.restaurant,
          isFavorited: false,
          FavoriteCount: this.restaurant.FavoriteCount - 1
        };
      } catch (error) {
        Toast.fire({
          icon: "error",
          title: "無法追蹤餐廳，請稍後再試"
        });
        console.log("error", error);
      }
    }
  }
};
</script>