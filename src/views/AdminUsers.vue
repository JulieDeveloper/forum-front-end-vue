<template>
  <div class="container py-5">
    <AdminNav />

    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th scope="col">#</th>
          <th scope="col">Email</th>
          <th scope="col">Role</th>
          <th scope="col" width="160">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.id">
          <th scope="row">{{ user.id }}</th>
          <td>{{ user.email }}</td>
          <td>{{ user.isAdmin? 'admin':'user' }}</td>
          <td>
            <button v-if="currentUser.id !== user.id" @click.stop.prevent="toggleUserRole(user.id)"  type="button" class="btn btn-link">
              set as {{ user.isAdmin ? 'user' : 'admin' }}
            </button>
            <button v-else @click.stop.prevent="toggleUserRole(user.id)"  type="button" class="btn btn-link">
              -
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import AdminNav from '../components/AdminNav.vue'
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
            "updatedAt": "2022-10-21T11:58:14.000Z"
        },
        {
            "id": 2,
            "name": "user1",
            "email": "user1@example.com",
            "password": "$2a$10$qMd2WAX5KCw.Z.KEENPxhuIsgXKfRh52IoOSBI6Hb1eG0hcCN2bZu",
            "isAdmin": false,
            "image": null,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z"
        },
        {
            "id": 3,
            "name": "user2",
            "email": "user2@example.com",
            "password": "$2a$10$PGrou.H0NZZLEYaLe2yvYOeL.m7n1CwH8B9iLqSB1SEuCPasKJLBG",
            "isAdmin": false,
            "image": null,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z"
        }
    ]
}
const dummyUser = {
  currentUser: {
    id: 1,
    name: '管理者',
    email: 'root@example.com',
    image: 'https://i.pravatar.cc/300',
    isAdmin: true
  },
  isAuthenticated: true
}

export default {
 components:{
  AdminNav,
 },
 data(){
  return{
    users:[],
    currentUser:{
      id: dummyUser.currentUser.id
    }
  }
 },
 created(){
  this.fetchUsers()
 },
 methods:{
  fetchUsers(){
    this.users = dummyData.users
  },
  toggleUserRole(userId){
    this.users = this.users.map(user => {
        if (user.id === userId) {
          return {
            ...user,
            isAdmin: !user.isAdmin
          }
        }
        return user
      })
  }
 }
}
</script>
