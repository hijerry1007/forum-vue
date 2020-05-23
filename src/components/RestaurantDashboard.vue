<template>
  <div class="container py-5">
    <div>
      <h1>{{restaurant.name }}</h1>
      <span class="badge badge-secondary mt-1 mb-3">{{ restaurant.categoryName }}</span>
    </div>

    <hr />

    <ul>
      <li>評論數： {{ restaurant.commentsLength }}</li>
      <li>瀏覽次數： {{ restaurant.viewCounts }}</li>
    </ul>

    <button type="button" class="btn btn-link" @click="$router.back()">回上一頁</button>
  </div>
</template>


<script>
export default {
  props: {
    restaurantData: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      restaurant: this.restaurantData
    };
  }
};
</script>