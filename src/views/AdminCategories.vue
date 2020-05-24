<template>
  <div class="container py-5">
    <!-- 1. 使用先前寫好的 AdminNav -->
    <AdminNav />

    <form class="my-4">
      <div class="form-row">
        <div class="col-auto">
          <input v-model="newCategoryName" type="text" class="form-control" placeholder="新增餐廳類別..." />
        </div>
        <div class="col-auto">
          <button type="button" class="btn btn-primary" @click.stop.prevent="createCategory()">新增</button>
        </div>
      </div>
    </form>
    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th scope="col" width="60">#</th>
          <th scope="col">Category Name</th>
          <th scope="col" width="210">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-show="!isLoading" v-for="category in categories" :key="category.id">
          <th scope="row">{{ category.id }}</th>
          <td class="position-relative">
            <div v-show="!category.isEditing" class="category-name">{{ category.name }}</div>
            <input
              v-show="category.isEditing"
              v-model="category.name"
              type="text"
              class="form-control"
            />
            <span v-show="category.isEditing" class="cancel" @click="handleCancel(category.id)">✕</span>
          </td>
          <td class="d-flex justify-content-between">
            <button
              v-show="!category.isEditing"
              type="button"
              class="btn btn-link mr-2"
              @click.stop.prevent="toggleIsEditing(category.id)"
            >Edit</button>
            <button
              v-show="category.isEditing"
              type="button"
              class="btn btn-link mr-2"
              @click.stop.prevent="updateCategory({ categoryId: category.id, name: category.name })"
              :disabled="isProcessing"
            >{{ isProcessing? '儲存中' : 'Save'}}</button>
            <button
              type="button"
              class="btn btn-link mr-2"
              @click.stop.prevent="deleteCategory(category.id)"
            >Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import AdminNav from "@/components/AdminNav";
import adminAPI from "../apis/admin";
import { Toast } from "./../utils/helpers";

export default {
  components: {
    AdminNav
  },
  data() {
    return {
      categories: [],
      newCategoryName: "",
      isProcessing: false,
      isLoading: true
    };
  },
  created() {
    this.fetchCategories();
  },
  methods: {
    async fetchCategories() {
      try {
        const { data } = await adminAPI.categories.get();
        this.categories = data.categories.map(category => ({
          ...category,
          isEditing: false,
          nameCached: ""
        }));
        this.isLoading = false;
      } catch (error) {
        this.isLoading = false;

        console.log("error", error);
        Toast.fire({
          icon: "error",
          title: "伺服器忙碌中，請稍後再試"
        });
      }
    },
    async createCategory() {
      try {
        this.isProcessing = true;
        const { data } = await adminAPI.categories.create({
          name: this.newCategoryName
        });
        if (data.status === "error") {
          throw new Error(data.message);
        }
        this.categories.push({
          id: data.categoryId,
          name: this.newCategoryName
        });
        this.newCategoryName = "";
        this.isProcessing = false;
      } catch (error) {
        console.log("error", error);
        Toast.fire({ icon: "error", title: "無法新增類別，請稍後再試" });
      }
    },
    async deleteCategory(categoryId) {
      try {
        const { data } = await adminAPI.categories.delete(categoryId);
        if (data.status === "error") {
          throw new Error(data.message);
        }
        this.categories = this.categories.filter(
          category => category.id !== categoryId
        );
      } catch (error) {
        console.log("error", error);
        Toast.fire({ icon: "error", title: "無法刪除，請重新再試" });
      }
    },
    toggleIsEditing(categoryId) {
      this.categories = this.categories.map(category => {
        if (category.id === categoryId) {
          return {
            ...category,
            isEditing: !category.isEditing,
            nameCached: category.name
          };
        }

        return category;
      });
    },
    async updateCategory({ categoryId, name }) {
      try {
        this.isProcessing = true;

        const { data } = await adminAPI.categories.update({
          categoryId: categoryId,
          name: name
        });
        if (data.status === "error") {
          throw new Error(data.message);
        }
        this.toggleIsEditing(categoryId);
        this.isProcessing = false;
      } catch (error) {
        console.log("error", error);
        Toast.fire({ icon: "error", title: "儲存失敗，請稍後再試" });
      }
    },
    handleCancel(categoryId) {
      this.categories = this.categories.map(category => {
        if (category.id === categoryId) {
          return {
            ...category,
            name: category.nameCached
          };
        }
        return category;
      });

      this.toggleIsEditing(categoryId);
    }
  }
};
</script>

<style scoped>
.category-name {
  padding: 0.375rem 0.75rem;
  border: 1px solid transparent;
  outline: 0;
  cursor: auto;
}

.btn-link {
  width: 62px;
}

.cancel {
  position: absolute;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 25px;
  height: 25px;
  border: 1px solid #aaaaaa;
  border-radius: 50%;
  user-select: none;
  cursor: pointer;
  font-size: 12px;
}
</style>