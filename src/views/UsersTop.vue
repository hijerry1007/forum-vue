<template >
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">美食達人</h1>
    <hr />
    <div class="row text-center">
      <UsersTopContent v-for="user in users" :key="user.id" :initial-user="user" />
    </div>
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";
import UsersTopContent from "../components/UsersTopContent.vue";
const dummyData = {
  users: [
    {
      id: 72,
      name: "mohammad akhbarati",
      email: "makhbarati@gmail.com",
      password: "$2a$10$ljaWKqtQwgLA5BdTEhBTHeJK/Ku4ow3IHM4S5OJYmr7.anBAIl7NW",
      isAdmin: true,
      image: null,
      createdAt: "2020-02-29T23:24:32.000Z",
      updatedAt: "2020-04-21T10:01:23.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 72,
            createdAt: "2020-03-25T07:42:57.000Z",
            updatedAt: "2020-03-25T07:42:57.000Z"
          }
        },
        {
          id: 3,
          name: "user2",
          email: "user2@example.com",
          password:
            "$2a$10$VHKmtPqbcUzK46qxLllqj.w506U2N2TObMmnpdlNG2CLZPa1xzuTi",
          isAdmin: true,
          image: "https://i.imgur.com/IaCnj2S.jpg",
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:44:01.000Z",
          Followship: {
            followerId: 3,
            followingId: 72,
            createdAt: "2020-03-30T04:25:20.000Z",
            updatedAt: "2020-03-30T04:25:20.000Z"
          }
        },
        {
          id: 322,
          name: "123",
          email: "123@123",
          password:
            "$2a$10$puJ.mSl6Xp6S0SByjQNjxe34k/TjTCHOQDh1yUnANo3U80xsarEf2",
          isAdmin: false,
          image: "https://i.imgur.com/dQq7Bvo.jpg",
          createdAt: "2020-04-07T08:23:03.000Z",
          updatedAt: "2020-04-07T15:29:59.000Z",
          Followship: {
            followerId: 322,
            followingId: 72,
            createdAt: "2020-04-07T15:31:22.000Z",
            updatedAt: "2020-04-07T15:31:22.000Z"
          }
        },
        {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$J9pLpJJ1Tzfe/ZcjdYwXdumyh.3F5E.w/HTxRcH./cl3azhgekgQe",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-03-02T17:09:40.000Z",
          Followship: {
            followerId: 1,
            followingId: 72,
            createdAt: "2020-05-15T13:08:53.000Z",
            updatedAt: "2020-05-15T13:08:53.000Z"
          }
        }
      ],
      FollowerCount: 4,
      isFollowed: true
    },
    {
      id: 102,
      name: "asd@asd.asd",
      email: "asd@asd.asd",
      password: "$2a$10$r9jgmPQGI2uN59XwkuTiX.qRORpqYDoMg8e36WJ.bw1JexPvpXVp.",
      isAdmin: false,
      image: "https://i.imgur.com/yJTFCDh.jpg",
      createdAt: "2020-03-09T06:15:49.000Z",
      updatedAt: "2020-03-09T06:16:09.000Z",
      Followers: [
        {
          id: 3,
          name: "user2",
          email: "user2@example.com",
          password:
            "$2a$10$VHKmtPqbcUzK46qxLllqj.w506U2N2TObMmnpdlNG2CLZPa1xzuTi",
          isAdmin: true,
          image: "https://i.imgur.com/IaCnj2S.jpg",
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:44:01.000Z",
          Followship: {
            followerId: 3,
            followingId: 102,
            createdAt: "2020-03-30T03:25:48.000Z",
            updatedAt: "2020-03-30T03:25:48.000Z"
          }
        },
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 102,
            createdAt: "2020-04-17T03:56:12.000Z",
            updatedAt: "2020-04-17T03:56:12.000Z"
          }
        },
        {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$J9pLpJJ1Tzfe/ZcjdYwXdumyh.3F5E.w/HTxRcH./cl3azhgekgQe",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-03-02T17:09:40.000Z",
          Followship: {
            followerId: 1,
            followingId: 102,
            createdAt: "2020-05-15T13:09:03.000Z",
            updatedAt: "2020-05-15T13:09:03.000Z"
          }
        }
      ],
      FollowerCount: 3,
      isFollowed: true
    },
    {
      id: 212,
      name: "jerry",
      email: "sccwcc106@gmail.com",
      password: "$2a$10$WJvYYwgXFeyqo86OX.bLDuXNN4XRmh4KOjJyuHvDEn6yxl.v4uQoS",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-24T14:04:29.000Z",
      updatedAt: "2020-03-24T14:04:29.000Z",
      Followers: [
        {
          id: 112,
          name: "測試",
          email: "123@example.com",
          password:
            "$2a$10$oJlwrpCT8jAC2Kamet775u3kNbd.SV85yvHH9c/L2bKODZ437Cn/K",
          isAdmin: false,
          image: null,
          createdAt: "2020-03-12T15:28:49.000Z",
          updatedAt: "2020-03-12T15:28:49.000Z",
          Followship: {
            followerId: 112,
            followingId: 212,
            createdAt: "2020-04-15T12:25:24.000Z",
            updatedAt: "2020-04-15T12:25:24.000Z"
          }
        },
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 212,
            createdAt: "2020-04-17T03:15:24.000Z",
            updatedAt: "2020-04-17T03:15:24.000Z"
          }
        },
        {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$J9pLpJJ1Tzfe/ZcjdYwXdumyh.3F5E.w/HTxRcH./cl3azhgekgQe",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-03-02T17:09:40.000Z",
          Followship: {
            followerId: 1,
            followingId: 212,
            createdAt: "2020-05-15T13:10:12.000Z",
            updatedAt: "2020-05-15T13:10:12.000Z"
          }
        }
      ],
      FollowerCount: 3,
      isFollowed: true
    },
    {
      id: 112,
      name: "測試",
      email: "123@example.com",
      password: "$2a$10$oJlwrpCT8jAC2Kamet775u3kNbd.SV85yvHH9c/L2bKODZ437Cn/K",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-12T15:28:49.000Z",
      updatedAt: "2020-03-12T15:28:49.000Z",
      Followers: [
        {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$J9pLpJJ1Tzfe/ZcjdYwXdumyh.3F5E.w/HTxRcH./cl3azhgekgQe",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-03-02T17:09:40.000Z",
          Followship: {
            followerId: 1,
            followingId: 112,
            createdAt: "2020-04-16T07:15:09.000Z",
            updatedAt: "2020-04-16T07:15:09.000Z"
          }
        },
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 112,
            createdAt: "2020-04-17T03:11:45.000Z",
            updatedAt: "2020-04-17T03:11:45.000Z"
          }
        }
      ],
      FollowerCount: 2,
      isFollowed: true
    },
    {
      id: 2,
      name: "user1",
      email: "user1@example.com",
      password: "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
      isAdmin: true,
      image: null,
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-04-21T09:59:58.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 2,
            createdAt: "2020-03-25T07:52:27.000Z",
            updatedAt: "2020-03-25T07:52:27.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 3,
      name: "user2",
      email: "user2@example.com",
      password: "$2a$10$VHKmtPqbcUzK46qxLllqj.w506U2N2TObMmnpdlNG2CLZPa1xzuTi",
      isAdmin: true,
      image: "https://i.imgur.com/IaCnj2S.jpg",
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-04-21T09:44:01.000Z",
      Followers: [
        {
          id: 242,
          name: "abc",
          email: "abc@abc",
          password:
            "$2a$10$seMk2.DnlqD708UVY3SAtuFpQcGMa9TwwR0BuHzeennUFxIBk1LnC",
          isAdmin: false,
          image: null,
          createdAt: "2020-03-26T08:03:08.000Z",
          updatedAt: "2020-03-26T08:03:08.000Z",
          Followship: {
            followerId: 242,
            followingId: 3,
            createdAt: "2020-03-30T01:31:47.000Z",
            updatedAt: "2020-03-30T01:31:47.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 62,
      name: "AC",
      email: "ac@ac.com",
      password: "$2a$10$yB01LxQAujWjRQ0WaprYV.t5SDx6kool5Cmrt0F7TRSXGRk.W8z1m",
      isAdmin: true,
      image: null,
      createdAt: "2020-02-29T15:41:09.000Z",
      updatedAt: "2020-04-21T10:00:59.000Z",
      Followers: [
        {
          id: 3,
          name: "user2",
          email: "user2@example.com",
          password:
            "$2a$10$VHKmtPqbcUzK46qxLllqj.w506U2N2TObMmnpdlNG2CLZPa1xzuTi",
          isAdmin: true,
          image: "https://i.imgur.com/IaCnj2S.jpg",
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:44:01.000Z",
          Followship: {
            followerId: 3,
            followingId: 62,
            createdAt: "2020-04-04T04:53:41.000Z",
            updatedAt: "2020-04-04T04:53:41.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 82,
      name: "aaa",
      email: "aaa@aaa",
      password: "$2a$10$tKDZYhuLyqqwiWqILKWygewD8m9w8LXtMVux1iRaa8CMVsWJa5ma.",
      isAdmin: true,
      image: null,
      createdAt: "2020-03-08T14:50:18.000Z",
      updatedAt: "2020-04-21T10:02:21.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 82,
            createdAt: "2020-04-17T03:48:39.000Z",
            updatedAt: "2020-04-17T03:48:39.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 92,
      name: "asdasd",
      email: "asdasd@asdasd.asdasd",
      password: "$2a$10$J4Z/hkxNtpZYM0mj/eCaM.bBRTtTC4yOwISf4d..ia9sdB0ym/9yO",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-08T17:38:03.000Z",
      updatedAt: "2020-03-08T17:38:03.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 92,
            createdAt: "2020-03-25T07:52:25.000Z",
            updatedAt: "2020-03-25T07:52:25.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 122,
      name: "user999",
      email: "user999@example.com",
      password: "$2a$10$ggSKzmB0Zf02M3bX5sJwc.oKeL.EyQgKBa99sRpNWi8Eqov6Cm0Xa",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-17T07:23:13.000Z",
      updatedAt: "2020-03-17T07:23:13.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 122,
            createdAt: "2020-04-17T03:16:31.000Z",
            updatedAt: "2020-04-17T03:16:31.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 132,
      name: "user888",
      email: "user888@example.com",
      password: "$2a$10$mOIkAG2UZ8jw5ErEUvtMneVkV.EDl71R9Ec1Va2wMymR5tCMyU3ve",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-17T07:50:53.000Z",
      updatedAt: "2020-03-17T07:50:53.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 132,
            createdAt: "2020-03-24T05:53:45.000Z",
            updatedAt: "2020-03-24T05:53:45.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 142,
      name: "user888",
      email: "user888@123.com",
      password: "$2a$10$c3.Mbs29E1s320x8zBZeGOF7csa0udo/wkht1sOPuNAPTTtw/YEUu",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-17T07:54:09.000Z",
      updatedAt: "2020-03-17T07:54:09.000Z",
      Followers: [
        {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$J9pLpJJ1Tzfe/ZcjdYwXdumyh.3F5E.w/HTxRcH./cl3azhgekgQe",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-03-02T17:09:40.000Z",
          Followship: {
            followerId: 1,
            followingId: 142,
            createdAt: "2020-04-08T15:35:07.000Z",
            updatedAt: "2020-04-08T15:35:07.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: true
    },
    {
      id: 152,
      name: "user777",
      email: "user777@example.com",
      password: "$2a$10$z6NW4BS/QVlChCPCESgK1OcmLNfgi1EocyEH3IzUVzu5zyIopyopC",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-17T08:03:35.000Z",
      updatedAt: "2020-03-17T08:03:35.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 152,
            createdAt: "2020-03-25T07:52:35.000Z",
            updatedAt: "2020-03-25T07:52:35.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 162,
      name: "test",
      email: "test@test.com",
      password: "$2a$10$HzCWQezkOs9jCssiW7tjD.tYyMrX0iVxpx.cx4vWJxqlbWZMREFm2",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-22T09:35:11.000Z",
      updatedAt: "2020-03-22T09:35:11.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 162,
            createdAt: "2020-03-25T06:35:02.000Z",
            updatedAt: "2020-03-25T06:35:02.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 172,
      name: "a",
      email: "a26620236@gmail.com",
      password: "$2a$10$hRVJ4Mr6uAlWj3I9q7a4G.Ghavo.ra5jmEvH6GY37rewVqg0fkxoS",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-23T10:29:12.000Z",
      updatedAt: "2020-03-23T10:29:12.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 172,
            createdAt: "2020-03-25T06:35:06.000Z",
            updatedAt: "2020-03-25T06:35:06.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 182,
      name: "lim jianhang",
      email: "nerflim@gmail.com",
      password: "$2a$10$Qz1PP5vYpcBwzCeaLELCiujLjId7SSyLUiyfP2TtM8suafrsAHGmW",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-23T15:21:31.000Z",
      updatedAt: "2020-03-23T15:21:31.000Z",
      Followers: [
        {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$J9pLpJJ1Tzfe/ZcjdYwXdumyh.3F5E.w/HTxRcH./cl3azhgekgQe",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-03-02T17:09:40.000Z",
          Followship: {
            followerId: 1,
            followingId: 182,
            createdAt: "2020-03-23T15:55:26.000Z",
            updatedAt: "2020-03-23T15:55:26.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: true
    },
    {
      id: 192,
      name: "Joey",
      email: "joeytan030306@gmail.com",
      password: "$2a$10$h63NLEefacJQPJ1xsAoMlu3zS0e9vn7lnezl6o9gQ0EAMvT9NrBrm",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-23T15:21:43.000Z",
      updatedAt: "2020-03-23T15:21:43.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 192,
            createdAt: "2020-03-23T23:46:44.000Z",
            updatedAt: "2020-03-23T23:46:44.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 202,
      name: "Agnes",
      email: "405322605@mail.fju.edu.tw",
      password: "$2a$10$4cBLm1YQI2NuWIfDDA/5YeTtINhe.m7NrnFCI044I9AYSZBDEWaqy",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-24T00:32:41.000Z",
      updatedAt: "2020-03-24T00:32:41.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 202,
            createdAt: "2020-04-17T03:48:44.000Z",
            updatedAt: "2020-04-17T03:48:44.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 282,
      name: "test",
      email: "test@test",
      password: "$2a$10$GcVlOi3hxPswn.KKehlVruWFoSuZXShWPY70cU2ixyPimdUoElXci",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-27T10:39:11.000Z",
      updatedAt: "2020-03-27T10:39:11.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NyaAtgRuHx3i7hHlnb5IXOC4Uk4.q1J1iQs3op.ymdCEh7.tOwcH2",
          isAdmin: true,
          image: null,
          createdAt: "2020-02-28T14:38:32.000Z",
          updatedAt: "2020-04-21T09:59:58.000Z",
          Followship: {
            followerId: 2,
            followingId: 282,
            createdAt: "2020-04-17T03:15:19.000Z",
            updatedAt: "2020-04-17T03:15:19.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 1,
      name: "root",
      email: "root@example.com",
      password: "$2a$10$J9pLpJJ1Tzfe/ZcjdYwXdumyh.3F5E.w/HTxRcH./cl3azhgekgQe",
      isAdmin: true,
      image: null,
      createdAt: "2020-02-28T14:38:32.000Z",
      updatedAt: "2020-03-02T17:09:40.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 222,
      name: null,
      email: "roott@expample.com",
      password: "$2a$10$q0vuZo.FC1C.j4g.q34kTuWIMbiDGRnW8CQfa2/iaTdfktDBRT5xq",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-24T16:35:42.000Z",
      updatedAt: "2020-03-24T16:35:42.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 232,
      name: "wbh",
      email: "ReadingExchange@163.com",
      password: "$2a$10$1h2OE3ZFUTR6Lr9bojp4ee2fxUBya/NpkwveJNxpe7h2JeFe6eb0a",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-25T15:53:23.000Z",
      updatedAt: "2020-03-25T15:53:23.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 242,
      name: "abc",
      email: "abc@abc",
      password: "$2a$10$seMk2.DnlqD708UVY3SAtuFpQcGMa9TwwR0BuHzeennUFxIBk1LnC",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-26T08:03:08.000Z",
      updatedAt: "2020-03-26T08:03:08.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 252,
      name: "abc2",
      email: "abc@abc2",
      password: "$2a$10$pIOhVJRAxBlK.KSkHWCVQeewHAYIRx.kwQuMxsFs4fa1lpgXK4X0i",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-26T08:17:51.000Z",
      updatedAt: "2020-03-26T08:17:51.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 262,
      name: "abc3",
      email: "abc@abc3",
      password: "$2a$10$7V2m5qZNLuEJNMvxOJdR9eFrcye9E1.rKeHPHPSO2.1NO/Ao8ej92",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-26T08:20:22.000Z",
      updatedAt: "2020-03-26T08:20:22.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 272,
      name: "abc4",
      email: "abc@abc4",
      password: "$2a$10$0Xb6KAJqFpyTL6TwCTGI8uRhlkbnfl11WsqDVIyQW.FGno21FN9h.",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-26T08:21:47.000Z",
      updatedAt: "2020-03-26T08:21:47.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 292,
      name: "test1",
      email: "test1@test",
      password: "$2a$10$0ChHNZrj8fuzuEl1oxm9deFu17i3wMHuXJbAG3lU55bk5e5FvL2VW",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-27T10:42:32.000Z",
      updatedAt: "2020-03-27T10:42:32.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 302,
      name: "test11",
      email: "test11@test",
      password: "$2a$10$RwJxX/2t1Y2nPyElnSyEKe00XCTt7i54G.WUYDrlRgqYftA.6gUGm",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-27T10:47:49.000Z",
      updatedAt: "2020-03-27T10:47:49.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 312,
      name: "test100",
      email: "test100@example.com",
      password: "$2a$10$.RYrFGtoUIgzwzxAHnNz2uR6MVbwmyvtPTcQwPWyHZDlGGYWFpiVS",
      isAdmin: false,
      image: null,
      createdAt: "2020-03-30T04:53:36.000Z",
      updatedAt: "2020-03-30T04:53:36.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 322,
      name: "123",
      email: "123@123",
      password: "$2a$10$puJ.mSl6Xp6S0SByjQNjxe34k/TjTCHOQDh1yUnANo3U80xsarEf2",
      isAdmin: false,
      image: "https://i.imgur.com/dQq7Bvo.jpg",
      createdAt: "2020-04-07T08:23:03.000Z",
      updatedAt: "2020-04-07T15:29:59.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 332,
      name: "wishfree",
      email: "wishfree76@gmail.com",
      password: "$2a$10$11XZtbdnc5DK.sEJbpzvE.TTUs0UDFBM1rOKQ7jgp.pHHZrRExaH6",
      isAdmin: false,
      image: null,
      createdAt: "2020-04-09T00:42:29.000Z",
      updatedAt: "2020-04-09T00:42:29.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 342,
      name: "sun",
      email: "sun@gmail.com",
      password: "$2a$10$HTLYE3NAIJ1KODNdTXXXs.8oFKo8vuzsPKhSnXS3eb8v6gv6okJre",
      isAdmin: false,
      image: null,
      createdAt: "2020-04-11T04:24:54.000Z",
      updatedAt: "2020-04-11T04:24:54.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 352,
      name: "my",
      email: "myname@name.name",
      password: "$2a$10$nHaozM7WZpf2GplWHg05RezJgoX2q8371l3RyYWL7Mi6cOAWsO1Ou",
      isAdmin: false,
      image: null,
      createdAt: "2020-04-13T07:30:19.000Z",
      updatedAt: "2020-04-13T07:30:19.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 362,
      name: "123",
      email: "123@qq.com",
      password: "$2a$10$Try7NBdnaedRekrdTiaM9uxrnGRAWVeYC3QHiWp0LLn0bq4E2xnbS",
      isAdmin: false,
      image: null,
      createdAt: "2020-05-01T08:45:05.000Z",
      updatedAt: "2020-05-01T08:45:05.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 372,
      name: "123",
      email: "123585858@qq.com",
      password: "$2a$10$rLkUFpz9zzlJ0bUhgCOawOg0qsjxzfHDsc6gLpPlxeort5IUT.ipO",
      isAdmin: false,
      image: null,
      createdAt: "2020-05-01T08:46:24.000Z",
      updatedAt: "2020-05-01T08:46:24.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 382,
      name: "Juan",
      email: "juan@example.com",
      password: "$2a$10$NXC.L5ovfIB.WW1jGMmc0uxEgLPsl7zNK4pfiCXf6AV9ZLOC/ew4u",
      isAdmin: false,
      image: null,
      createdAt: "2020-05-16T06:53:12.000Z",
      updatedAt: "2020-05-16T06:53:12.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    }
  ]
};
export default {
  components: {
    NavTabs,
    UsersTopContent
  },
  data() {
    return {
      users: []
    };
  },
  created() {
    this.fetchUsers();
  },
  methods: {
    fetchUsers() {
      this.users = dummyData.users;
    }
  }
};
</script>