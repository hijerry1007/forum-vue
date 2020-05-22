<template>
  <div class="container py-5">
    <!-- use NavTabs -->
    <NavTabs />
    <!-- 餐廳類別標籤 RestaurantsNavPills -->
    <RestaurantsNavPills :categories="categories" />
    <div class="row">
      <!-- 餐廳卡片 -->
      <RestaurantCard
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initial-restaurant="restaurant"
      />
    </div>

    <!-- 分頁標籤 -->
    <RestaurantsPagination
      v-if="totalPage.length > 1"
      :current-page="currentPage"
      :total-page="totalPage"
      :category-id="categoryId"
      :previous-page="previousPage"
      :next-page="nextPage"
    />
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";
import RestaurantCard from "../components/RestaurantCard.vue";
import RestaurantsNavPills from "../components/RestaurantsNavPills.vue";
import RestaurantsPagination from "../components/RestaurantsPagination";

const dummyData = {
  restaurants: [
    {
      id: 5,
      name: "Mitchel Beatty",
      tel: "171-324-8413",
      address: "85408 Francisca Square",
      opening_hours: "08:00",
      description: "Aut cumque excepturi exercitationem libero volupta",
      image: "https://i.imgur.com/awJFBLn.jpg",
      viewCounts: 276,
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-05-21T10:34:24.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z"
      },
      isFavorited: true,
      isLiked: false
    },
    {
      id: 6,
      name: "Vicenta Gutkowski Test By Nacho",
      tel: "128-905-3953",
      address: "371 Reuben Vista test",
      opening_hours: "00:00",
      description: "labore",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=16.659471621888123",
      viewCounts: 45,
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-05-19T06:28:37.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z"
      },
      isFavorited: true,
      isLiked: false
    },
    {
      id: 7,
      name: "Miss Letitia Will",
      tel: "(770) 750-6811 x99988",
      address: "8145 Laisha Keys",
      opening_hours: "08:00",
      description: "Aut earum molestiae et ducimus adipisci ut maxime.",
      image: "https://i.imgur.com/50clDpn.jpg",
      viewCounts: 89,
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-05-19T06:28:30.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z"
      },
      isFavorited: false,
      isLiked: true
    },
    {
      id: 9,
      name: "Luz Schaden",
      tel: "1-712-742-4184",
      address: "4929 Wisozk Centers",
      opening_hours: "08:00",
      description: "Culpa deserunt molestiae eligendi est ex incidunt.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=6.497835218728576",
      viewCounts: 31,
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-04-22T06:18:59.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z"
      },
      isFavorited: true,
      isLiked: false
    },
    {
      id: 10,
      name: "Corbin Gusikowski",
      tel: "(506) 198-3977",
      address: "4747 Lubowitz Brook",
      opening_hours: "08:00",
      description: "Aut quia aut ea nostrum quae doloremque necessitat",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=6.84802493817025",
      viewCounts: 31,
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-04-11T08:35:22.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z"
      },
      isFavorited: false,
      isLiked: false
    },
    {
      id: 11,
      name: "Vergie Considine",
      tel: "351.951.8030 x0330",
      address: "8865 Conrad Mill",
      opening_hours: "08:00",
      description: "Quia omnis natus est praesentium dolores aliquid d",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=0.7508871784973614",
      viewCounts: 1,
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-03-09T06:09:15.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z"
      },
      isFavorited: true,
      isLiked: false
    },
    {
      id: 12,
      name: "Oliver Padberg",
      tel: "865-523-0270 x58016",
      address: "771 Oberbrunner Hollow",
      opening_hours: "08:00",
      description: "Magni qui facilis asperiores. Voluptatem cumque co",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=22.348939427568215",
      viewCounts: 5,
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-04-10T10:48:16.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-05-17T03:45:22.000Z"
      },
      isFavorited: false,
      isLiked: false
    },
    {
      id: 13,
      name: "Mrs. Eileen Lockman",
      tel: "(597) 404-9974 x003",
      address: "383 Stroman Center",
      opening_hours: "08:00",
      description: "Vitae id incidunt animi qui sapiente perferendis i",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=54.950245749491145",
      viewCounts: 7,
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-04-11T03:56:01.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z"
      },
      isFavorited: false,
      isLiked: false
    },
    {
      id: 14,
      name: "Boyd Abbott",
      tel: "172-684-6335",
      address: "50119 Nader Via",
      opening_hours: "08:00",
      description: "Aut aut enim sint sed. Vero qui voluptas voluptate",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=67.78299128798855",
      viewCounts: 7419,
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-04-08T09:14:01.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z"
      },
      isFavorited: false,
      isLiked: false
    },
    {
      id: 16,
      name: "Aaliyah Lakin",
      tel: "1-235-923-9473 x43870",
      address: "1951 Jakubowski Villages",
      opening_hours: "08:00",
      description: "quidem",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=91.06034163072859",
      viewCounts: 9,
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-04-11T04:16:08.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z"
      },
      isFavorited: false,
      isLiked: false
    }
  ],
  categories: [
    {
      id: 1,
      name: "中式料理",
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-05-17T03:45:22.000Z"
    },
    {
      id: 2,
      name: "日本料理",
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-02-28T14:38:32.000Z"
    },
    {
      id: 3,
      name: "義大利料理",
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-02-28T14:38:32.000Z"
    },
    {
      id: 4,
      name: "墨西哥料理",
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-02-28T14:38:32.000Z"
    },
    {
      id: 5,
      name: "素食料理",
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-02-28T14:38:32.000Z"
    },
    {
      id: 6,
      name: "美式料理",
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-04-07T09:46:10.000Z"
    },
    {
      id: 1592,
      name: "dark cousine",
      createdAt: "2020-05-17T03:28:54.000Z",
      updatedAt: "2020-05-17T03:46:06.000Z"
    }
  ],
  page: 1,
  totalPage: [1, 2, 3, 4, 5],
  prev: 1,
  next: 2,
  categoryId: ""
};
export default {
  components: {
    NavTabs,
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantsPagination
  },
  data() {
    return {
      restaurants: [],
      categories: [],
      categoryId: -1,
      currentPage: 1,
      totalPage: [],
      previousPage: -1,
      nextPage: -1
    };
  },
  created() {
    this.fetchRestaurants();
  },
  methods: {
    fetchRestaurants() {
      const {
        restaurants,
        categories,
        categoryId,
        page,
        totalPage,
        prev,
        next
      } = dummyData;
      this.restaurants = restaurants;
      this.categories = categories;
      this.categoryId = categoryId;
      this.currentPage = page;
      this.totalPage = totalPage;
      this.previousPage = prev;
      this.nextPage = next;
    }
  }
};
</script>