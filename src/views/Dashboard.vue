<template>
  <RestaurantDashboard :restaurant-data="restaurant" />
</template>

<script>
import RestaurantDashboard from "../components/RestaurantDashboard";

const dummyData = {
  restaurant: {
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
    Comments: [
      {
        id: 16,
        text: "Harum illo molestiae.",
        UserId: 3,
        RestaurantId: 16,
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z",
        User: {
          id: 3,
          name: "user2",
          email: "user2@example.com",
          password:
            "$2a$10$VHKmtPqbcUzK46qxLllqj.w506U2N2TObMmnpdlNG2CLZPa1xzuTi",
          isAdmin: true,
          image: "https://i.imgur.com/IaCnj2S.jpg",
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:44:01.000Z"
        }
      },
      {
        id: 66,
        text: "Laudantium eum vel id.",
        UserId: 2,
        RestaurantId: 16,
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z",
        User: {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z"
        }
      },
      {
        id: 116,
        text: "Sunt culpa ad sed ea.",
        UserId: 3,
        RestaurantId: 16,
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z",
        User: {
          id: 3,
          name: "user2",
          email: "user2@example.com",
          password:
            "$2a$10$VHKmtPqbcUzK46qxLllqj.w506U2N2TObMmnpdlNG2CLZPa1xzuTi",
          isAdmin: true,
          image: "https://i.imgur.com/IaCnj2S.jpg",
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:44:01.000Z"
        }
      },
      {
        id: 4432,
        text: "delicious!",
        UserId: 1,
        RestaurantId: 16,
        createdAt: "2020-04-11T03:56:14.000Z",
        updatedAt: "2020-04-11T03:56:14.000Z",
        User: {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$J9pLpJJ1Tzfe/ZcjdYwXdumyh.3F5E.w/HTxRcH./cl3azhgekgQe",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-03-02T17:09:40.000Z"
        }
      }
    ]
  }
};
export default {
  components: {
    RestaurantDashboard
  },
  data() {
    return {
      restaurant: {}
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      this.restaurant = {
        ...dummyData.restaurant,
        categoryName: dummyData.restaurant.Category.name,
        commentsLength: dummyData.restaurant.Comments.length
      };
    }
  }
};
</script>