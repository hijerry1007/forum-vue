<template>
  <div class="col-3">
    <router-link :to="'/users/'+user.id">
      <img :src="user.image" width="140px" height="140px" />
    </router-link>
    <h2>{{user.name}}</h2>
    <span class="badge badge-secondary">追蹤人數：{{user.followerCount}}</span>
    <p class="mt-3">
      <button
        v-if="user.isFollowed"
        type="button"
        class="btn btn-danger"
        @click.stop.prevent="deleteFollow(user.id)"
      >取消追蹤</button>
      <button
        v-else
        type="button"
        class="btn btn-primary"
        @click.stop.prevent="addFollow(user.id)"
      >追蹤</button>
    </p>
  </div>
</template>

<script>
import usersAPI from "../apis/users";
import { Toast } from "../utils/helpers";
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
    async addFollow(userId) {
      try {
        const { data } = await usersAPI.addFollowing({ userId });

        console.log("data", data);

        if (data.status !== "success") {
          throw new Error(data.message);
        }
        if (this.user.id !== userId) {
          return this.user;
        } else {
          this.user = {
            ...this.user,
            followerCount: this.user.followerCount + 1,
            isFollowed: true
          };
        }
      } catch (error) {
        Toast.fire({
          icon: "error",
          title: "無法加入追蹤，請稍後再試"
        });
      }
    },
    async deleteFollow(userId) {
      try {
        const { data } = await usersAPI.deleteFollowing({ userId });

        if (data.status !== "success") {
          throw new Error(data.message);
        }

        if (this.user.id !== userId) {
          return this.user;
        } else {
          this.user = {
            ...this.user,
            followerCount: this.user.followerCount - 1,
            isFollowed: false
          };
        }
      } catch (error) {
        Toast.fire({
          icon: "error",
          title: "無法取消追蹤，請稍後再試"
        });
      }
    }
  }
};
</script>
  