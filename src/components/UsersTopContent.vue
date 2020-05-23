<template>
  <div class="row text-center">
    <div class="col-3">
      <router-link :to="'/users/'+user.id">
        <img :src="user.image" width="140px" height="140px" />
      </router-link>
      <h2>{{user.name}}</h2>
      <span class="badge badge-secondary">追蹤人數：{{user.Followers.length}}</span>
      <p class="mt-3">
        <button
          v-if="user.isFollowed"
          type="button"
          class="btn btn-danger"
          @click.stop.prevent="deleteFollow"
        >取消追蹤</button>
        <button v-else type="button" class="btn btn-primary" @click.stop.prevent="addFollow">追蹤</button>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    initialUser: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      user: this.initialUser
    };
  },
  methods: {
    addFollow() {
      this.user = {
        ...this.user,
        isFollowed: true
      };
    },
    deleteFollow() {
      this.user = {
        ...this.user,
        isFollowed: false
      };
    }
  }
};
</script>
  