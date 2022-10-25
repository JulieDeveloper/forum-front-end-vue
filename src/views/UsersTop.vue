<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">Top User</h1>
    <hr>
    <div class = "row text-center">
      <div 
        class="col-3"
        v-for = "user in users" 
        :key = "user.id"
      >
        <a href="#">
          <img
            src="user.image"
            width="140px"
            height="140px"
          >
        </a>
        <h2>{{ user.name }}</h2>
        <span class="badge badge-secondary">{{ user.FollowerCount }}
 Followers</span>
        <p class="mt-3">
          <button
            type="button"
            class="btn btn-danger mr-2"
            v-if="user.isFollowed"
            @click.stop.prevent="unfollowUser(user.id)"
          >
            UnFollow
          </button>
          <button
            type="button"
            class="btn btn-primary"
            @click.stop.prevent="followUser(user.id)"
            v-else
          >
            Follow
          </button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";

const dummyData = {
    "users": [
        {
            "id": 1,
            "name": "root",
            "email": "root@example.com",
            "password": "$2a$10$hU92lxKGfm.NRehuKL00G.f4Ira6jwr5dbAUFNQulqiK18EGhMdUm",
            "isAdmin": true,
            "image": null,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "Followers": [],
            "FollowerCount": 5,
            "isFollowed": true
        },
        {
            "id": 2,
            "name": "user1",
            "email": "user1@example.com",
            "password": "$2a$10$qMd2WAX5KCw.Z.KEENPxhuIsgXKfRh52IoOSBI6Hb1eG0hcCN2bZu",
            "isAdmin": false,
            "image": null,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "Followers": [],
            "FollowerCount": 13,
            "isFollowed": false
        },
        {
            "id": 3,
            "name": "user2",
            "email": "user2@example.com",
            "password": "$2a$10$PGrou.H0NZZLEYaLe2yvYOeL.m7n1CwH8B9iLqSB1SEuCPasKJLBG",
            "isAdmin": false,
            "image": null,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "Followers": [],
            "FollowerCount": 9,
            "isFollowed": false
        }
    ]
}

export default {
  components: {
    NavTabs,
  },
  data(){
    return {
      users: []
    }
  },
  created(){
    this.fetchUsers()
  },
  methods:{
    fetchUsers(){
      const { users } = dummyData
      this.users = users
    },
    followUser(id){
      this.users.forEach(user => {
        if(user.id === id){
          return user.isFollowed = true
        }
      })
    },
    unfollowUser(id){
      this.users.forEach(user => {
        if(user.id === id){
          return user.isFollowed = false
        }
      })
    }
  }
};
</script>
