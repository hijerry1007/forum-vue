<template>
  <div class="container py-5">
    <AdminNav />
    <!-- AdminNav Component -->

    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th scope="col">#</th>
          <th scope="col">Email</th>
          <th scope="col">Role</th>
          <th scope="col" width="140">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.id">
          <th scope="row">{{user.id}}</th>
          <td>{{user.email}}</td>
          <td v-show="user.isAdmin">admin</td>
          <td v-show="!user.isAdmin">user</td>
          <td v-show="user.isAdmin">
            <p v-if="currentUser.id === user.id">當前使用者</p>
            <button
              v-else
              type="button"
              class="btn btn-link"
              @click.stop.prevent="toggleIsAdmin({userId: user.id, isAdmin: user.isAdmin})"
            >set as user</button>
          </td>
          <td v-show="!user.isAdmin">
            <button
              type="button"
              class="btn btn-link"
              @click.stop.prevent="toggleIsAdmin({userId: user.id, isAdmin: user.isAdmin})"
            >set as admin</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import AdminNav from "../components/AdminNav";
import adminAPI from "../apis/admin";
import { mapState } from "vuex";
import { Toast } from "./../utils/helpers";

export default {
  components: {
    AdminNav
  },
  data() {
    return {
      users: [],
      isLoading: true
    };
  },
  computed: {
    ...mapState(["currentUser"])
  },
  created() {
    this.fetchUsers();
  },
  methods: {
    async fetchUsers() {
      try {
        this.isLoading = true;
        const { data } = await adminAPI.users.get();
        if (data.status === "error") {
          throw new Error(data.message);
        }
        this.users = data.users;
        this.isLoading = false;
      } catch (error) {
        console.error(error.message);
        this.isLoading = false;
        Toast.fire({
          icon: "error",
          title: "無法取得會員資料，請稍後再試"
        });
      }
    },
    async toggleIsAdmin({ userId, isAdmin }) {
      try {
        const { data } = await adminAPI.users.update({
          userId,
          isAdmin: (!isAdmin).toString()
        });
        if (data.status === "error") {
          throw new Error(data.message);
        }
        this.users = this.users.map(user => {
          if (user.id === userId) {
            return {
              ...user,
              isAdmin: !isAdmin
            };
          }
          return user;
        });
      } catch (error) {
        console.error(error.message);
        Toast.fire({
          icon: "error",
          title: "無法更新會員角色，請稍後再試"
        });
      }
    }
  }
};
</script>