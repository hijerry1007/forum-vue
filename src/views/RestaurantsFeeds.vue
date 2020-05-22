<template>
  <div class="container py-5">
    <!-- use NavTabs -->
    <NavTabs />
    <h1 class="mt-5">最新動態</h1>
    <hr />
    <div class="row">
      <div class="col-md-6">
        <h3>最新餐廳</h3>
        <!-- 最新餐廳 NewestRestaurants -->
        <NewestRestaurants :restaurants="restaurants" />
      </div>
      <div class="col-md-6">
        <!-- 最新評論 NewestComments-->
        <h3>最新評論</h3>
        <NewestComments :comments="comments" />
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";
import NewestRestaurants from "../components/NewestRestaurants";
import NewestComments from "../components/NewestComments";

const dummyData = {
  restaurants: [
    {
      id: 1852,
      name: "louisa",
      tel: "test",
      address: "test address",
      opening_hours: "08:00",
      description: "Americana",
      image: "https://i.imgur.com/Pg85Ryo.jpg",
      viewCounts: 0,
      createdAt: "2020-05-16T02:51:53.000Z",
      updatedAt: "2020-05-16T02:51:53.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-02-28T14:38:32.000Z"
      }
    },
    {
      id: 5,
      name: "Mitchel Beatty",
      tel: "171-324-8413",
      address: "85408 Francisca Square",
      opening_hours: "08:00",
      description:
        "Aut cumque excepturi exercitationem libero voluptates impedit. Enim animi repellendus tempora doloremque. Esse in delectus sequi ullam sed animi.",
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
      }
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
      }
    },
    {
      id: 7,
      name: "Miss Letitia Will",
      tel: "(770) 750-6811 x99988",
      address: "8145 Laisha Keys",
      opening_hours: "08:00",
      description:
        "Aut earum molestiae et ducimus adipisci ut maxime.\r\nVeritatis labore illum et similique cumque qui qui officia omnis.\r\nQui laudantium amet enim natus.\r\nVoluptatem quia est nam ut esse et.",
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
      }
    },
    {
      id: 9,
      name: "Luz Schaden",
      tel: "1-712-742-4184",
      address: "4929 Wisozk Centers",
      opening_hours: "08:00",
      description:
        "Culpa deserunt molestiae eligendi est ex incidunt.\nNisi sit totam.",
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
      }
    },
    {
      id: 10,
      name: "Corbin Gusikowski",
      tel: "(506) 198-3977",
      address: "4747 Lubowitz Brook",
      opening_hours: "08:00",
      description:
        "Aut quia aut ea nostrum quae doloremque necessitatibus. Eos illo quia et. Culpa repellat eos minus necessitatibus aut debitis accusamus.\n \rAssumenda aut itaque corrupti soluta et aut est. Hic non dignissimos odit qui. Optio doloribus rerum molestiae dolorem commodi. Culpa et officiis.\n \rCulpa laborum ea eos praesentium enim quasi eos. Nobis praesentium maxime soluta delectus eveniet reiciendis aut. Voluptates nesciunt et explicabo.",
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
      }
    },
    {
      id: 11,
      name: "Vergie Considine",
      tel: "351.951.8030 x0330",
      address: "8865 Conrad Mill",
      opening_hours: "08:00",
      description:
        "Quia omnis natus est praesentium dolores aliquid debitis omnis molestias.",
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
      }
    },
    {
      id: 12,
      name: "Oliver Padberg",
      tel: "865-523-0270 x58016",
      address: "771 Oberbrunner Hollow",
      opening_hours: "08:00",
      description:
        "Magni qui facilis asperiores. Voluptatem cumque corrupti ea at voluptatem. Assumenda esse esse fuga autem dolor qui. Veniam qui eius vero magnam ut inventore magni est.",
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
      }
    },
    {
      id: 13,
      name: "Mrs. Eileen Lockman",
      tel: "(597) 404-9974 x003",
      address: "383 Stroman Center",
      opening_hours: "08:00",
      description:
        "Vitae id incidunt animi qui sapiente perferendis iusto. Nemo placeat ut voluptas quae cupiditate eligendi. Expedita laborum vitae nulla quia ipsam. Et sunt a veniam culpa asperiores qui culpa. Odit reiciendis dolore reprehenderit est est voluptas ut rerum.  dddddd",
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
      }
    },
    {
      id: 14,
      name: "Boyd Abbott",
      tel: "172-684-6335",
      address: "50119 Nader Via",
      opening_hours: "08:00",
      description:
        "Aut aut enim sint sed. Vero qui voluptas voluptatem velit aut et numquam. Aut nesciunt sed aliquam. Non pariatur deserunt est. Quod illo dolorem sint et inventore culpa veritatis libero a.",
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
      }
    }
  ],
  comments: [
    {
      id: 4632,
      text: "djakjalj",
      UserId: 1,
      RestaurantId: 7,
      createdAt: "2020-05-19T05:49:31.000Z",
      updatedAt: "2020-05-19T05:49:31.000Z",
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
      },
      Restaurant: {
        id: 7,
        name: "Miss Letitia Will",
        tel: "(770) 750-6811 x99988",
        address: "8145 Laisha Keys",
        opening_hours: "08:00",
        description:
          "Aut earum molestiae et ducimus adipisci ut maxime.\r\nVeritatis labore illum et similique cumque qui qui officia omnis.\r\nQui laudantium amet enim natus.\r\nVoluptatem quia est nam ut esse et.",
        image: "https://i.imgur.com/50clDpn.jpg",
        viewCounts: 89,
        createdAt: "2020-02-28T14:38:32.000Z",
        updatedAt: "2020-05-19T06:28:30.000Z",
        CategoryId: 5
      }
    },
    {
      id: 4562,
      text: null,
      UserId: 1,
      RestaurantId: null,
      createdAt: "2020-05-19T04:44:39.000Z",
      updatedAt: "2020-05-19T04:44:39.000Z",
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
      },
      Restaurant: null
    },
    {
      id: 4552,
      text: null,
      UserId: 1,
      RestaurantId: null,
      createdAt: "2020-05-19T04:43:54.000Z",
      updatedAt: "2020-05-19T04:43:54.000Z",
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
      },
      Restaurant: null
    },
    {
      id: 4542,
      text: null,
      UserId: 1,
      RestaurantId: null,
      createdAt: "2020-05-19T04:25:32.000Z",
      updatedAt: "2020-05-19T04:25:32.000Z",
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
      },
      Restaurant: null
    },
    {
      id: 4532,
      text: null,
      UserId: 1,
      RestaurantId: null,
      createdAt: "2020-05-19T04:23:53.000Z",
      updatedAt: "2020-05-19T04:23:53.000Z",
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
      },
      Restaurant: null
    },
    {
      id: 4522,
      text: null,
      UserId: 1,
      RestaurantId: null,
      createdAt: "2020-05-19T04:23:40.000Z",
      updatedAt: "2020-05-19T04:23:40.000Z",
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
      },
      Restaurant: null
    },
    {
      id: 4512,
      text: "asf",
      UserId: 2,
      RestaurantId: null,
      createdAt: "2020-04-22T06:12:26.000Z",
      updatedAt: "2020-04-22T06:12:26.000Z",
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
      },
      Restaurant: null
    },
    {
      id: 4502,
      text: "ddd",
      UserId: 2,
      RestaurantId: null,
      createdAt: "2020-04-22T06:11:16.000Z",
      updatedAt: "2020-04-22T06:11:16.000Z",
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
      },
      Restaurant: null
    },
    {
      id: 4492,
      text: "ddd",
      UserId: 2,
      RestaurantId: null,
      createdAt: "2020-04-22T06:11:10.000Z",
      updatedAt: "2020-04-22T06:11:10.000Z",
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
      },
      Restaurant: null
    },
    {
      id: 4482,
      text: "ddd",
      UserId: 2,
      RestaurantId: null,
      createdAt: "2020-04-22T06:11:10.000Z",
      updatedAt: "2020-04-22T06:11:10.000Z",
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
      },
      Restaurant: null
    }
  ]
};
export default {
  components: {
    NavTabs,
    NewestRestaurants,
    NewestComments
  },
  data() {
    return {
      restaurants: [],
      comments: []
    };
  },
  created() {
    this.fetchFeeds();
  },
  methods: {
    fetchFeeds() {
      this.restaurants = dummyData.restaurants;
      this.comments = dummyData.comments.filter(
        comment => comment.Restaurant && comment.text
      );
    }
  }
};
</script>