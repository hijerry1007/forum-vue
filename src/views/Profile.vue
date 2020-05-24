<template>
  <div class="container py-5">
    <!-- user info -->
    <UserProfileCard
      :user="user"
      :initial-is-followed="isFollowed"
      :is-current-user="currentUser.id=== user.id"
    />
    <div class="row">
      <div class="col-md-4">
        <!-- following info -->
        <UserFollowingCard :user-following="user.Followings" />
        <!-- follower info -->
        <UserFollowerCard :user-followers="user.Followers" />
      </div>
      <div class="col-md-8">
        <!-- comment info -->
        <UserCommentCard :user-comments="user.Comments" />
        <!-- fovrite info -->
        <UserFavoriteCard :user-favoritedrestaurants="user.FavoritedRestaurants" />
      </div>
    </div>
  </div>
</template>

<script>
import UserProfileCard from "../components/UserProfileCard";
import UserFollowingCard from "../components/UserFollowingCard";
import UserFollowerCard from "../components/UserFollowerCard";
import UserCommentCard from "../components/UserCommentCard";
import UserFavoriteCard from "../components/UserFavoriteCard";

import usersAPI from "../apis/users";
import { Toast } from "./../utils/helpers";
import { mapState } from "vuex";

export default {
  components: {
    UserProfileCard,
    UserFollowingCard,
    UserFollowerCard,
    UserCommentCard,
    UserFavoriteCard
  },
  data() {
    return {
      user: {
        id: 0,
        image: "",
        name: "",
        email: "",
        followingsLength: 0,
        followersLength: 0,
        commentsLength: 0,
        favoritedRestaurantsLength: 0
      },
      isFollowed: false,
      followings: [],
      followers: [],
      comments: [],
      favoritedRestaurants: []
    };
  },
  computed: {
    ...mapState(["currentUser"])
  },
  created() {
    const { id: userId } = this.$route.params;
    this.fetchData(userId);
  },
  beforeRouteUpdate(to, from, next) {
    const { id } = to.params;
    this.fetchData(id);
    next();
  },
  methods: {
    async fetchData(userId) {
      try {
        const { data } = await usersAPI.get({ userId });
        if (data.status === "error") {
          throw new Error(data.message);
        }

        const { profile, isFollowed } = data;
        const {
          id,
          image,
          name,
          email,
          Followings,
          Followers,
          Comments,
          FavoritedRestaurants
        } = profile;

        const commentSet = new Set();
        this.comments = Comments.filter(
          comment =>
            comment.Restaurant &&
            !commentSet.has(comment.Restaurant.id) &&
            commentSet.add(comment.Restaurant.id)
        );

        this.user = {
          ...this.user,
          id,
          image,
          name,
          email,
          followingsLength: Followings.length,
          followersLength: Followers.length,
          commentsLength: this.comments.length,
          favoritedRestaurantsLength: FavoritedRestaurants.length
        };

        this.isFollowed = isFollowed;
        this.followings = Followings;
        this.followers = Followers;
        this.favoritedRestaurants = FavoritedRestaurants;
      } catch (error) {
        console.log(error);
        Toast.fire({
          icon: "error",
          title: "伺服器忙碌中"
        });
      }
    }
  }
};
</script>