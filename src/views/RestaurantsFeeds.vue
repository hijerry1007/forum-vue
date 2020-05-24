<template>
  <div class="container py-5">
    <!-- use NavTabs -->
    <NavTabs />
    <Spinner v-if="isLoading" />
    <h1 class="mt-5">最新動態</h1>
    <hr />
    <div class="row">
      <div class="col-md-6">
        <h3>最新餐廳</h3>
        <!-- 最新餐廳 NewestRestaurants -->
        <NewestRestaurants :restaurants="restaurants" />
      </div>
      <div class="col-md-6">
        <!-- 最新評論 NewestComments-->
        <h3>最新評論</h3>
        <NewestComments :comments="comments" />
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";
import NewestRestaurants from "../components/NewestRestaurants";
import NewestComments from "../components/NewestComments";
import restaurantsFeedsAPI from "../apis/restaurantsFeeds";
import { Toast } from "../utils/helpers";
import Spinner from "../components/Spinner";

export default {
  components: {
    NavTabs,
    NewestRestaurants,
    NewestComments,
    Spinner
  },
  data() {
    return {
      restaurants: [],
      comments: [],
      isLoading: true
    };
  },
  created() {
    this.fetchFeeds();
  },
  methods: {
    async fetchFeeds() {
      try {
        const response = await restaurantsFeedsAPI.getRestaurantsFeeds();

        const { restaurants, comments } = response.data;
        this.restaurants = restaurants;
        this.comments = comments.filter(
          comment => comment.Restaurant && comment.text
        );
        this.isLoading = false;
      } catch (error) {
        this.isLoading = false;

        Toast.fire({
          icon: "error",
          title: "伺服器忙碌中"
        });
        console.log("err", error);
      }
    }
  }
};
</script>