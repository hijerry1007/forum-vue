<template>
  <div class="container py-5">
    <UserEditForm :initial-user="user" @after-submit="handleAfterSubmit" />
  </div>
</template>

<script>
import UserEditForm from "../components/UserEditForm";
const dummyUser = {
  currentUser: {
    id: 1,
    name: "管理者",
    email: "root@example.com",
    image: "https://i.pravatar.cc/300",
    isAdmin: true
  }
};
export default {
  components: {
    UserEditForm
  },
  data() {
    return {
      user: {
        id: "",
        name: "",
        email: "",
        image: "",
        isAdmin: false
      }
    };
  },
  created() {
    const { id } = this.$route.params;
    this.fetchUser(id);
  },
  methods: {
    fetchUser(userId) {
      console.log("fetchUser id:", userId);
      this.user = dummyUser.currentUser;
      console.log(this.user);
    },
    handleAfterSubmit(formData) {
      for (let [name, value] of formData.entries()) {
        console.log(name + ": " + value);
      }
    }
  }
};
</script>