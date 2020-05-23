
<template>
  <div class="card">
    <div class="card-header">
      <strong>{{ followers.length }}</strong> followers (追隨者)
    </div>
    <div class="card-body">
      <router-link
        v-for="follower in followers"
        :key="follower.id"
        :to="{ name: 'user', params: { id: follower.id } }"
      >
        <img :src="follower.image | emptyImage" width="60" height="60" class="mr-1" />
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    userFollowers: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      followers: this.userFollowers
    };
  }
};
</script>