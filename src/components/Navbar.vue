<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <nav class="navbar navbar-expand-lg fixed-top navbar-dark bg-dark">
    <router-link class="navbar-brand" to="/"> Restaurant Forum </router-link>

    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon" />
    </button>

    <div id="navbarSupportedContent" class="navbar-collapse collapse">
      <div class="ml-auto d-flex align-items-center">
        <!-- user === admin -->
        <router-link
          v-if="currentUser.isAdmin"
          to="/admin"
          class="text-white mr-3"
        >
          Backstage
        </router-link>

        <!-- user === login -->
        <template v-if="isAuthenticated">
          <router-link :to=" { name: 'user', params: {id: currentUser.id} }" class="text-white mr-3"> 
            {{ currentUser.name || "User" }} Hello!
          </router-link>
          <button
            type="button"
            class="btn btn-sm btn-outline-success my-2 my-sm-0"
          >
            Log Out
          </button>
        </template>
      </div>
    </div>
  </nav>
</template>

<script>
// seed data
const dummyUser = { 
  currentUser: { 
    id: 1, 
    name: 'Admin', 
    email:'root@example.com', 
    image: 'https://i.pravatar.cc/300', 
    isAdmin: true 
  },
  isAuthenticated: true 
}

export default {
  data () {
    return {
      currentUser: { 
        id: -1, 
        name: '', 
        email: '', 
        image: '', 
        isAdmin: false 
      },
      isAuthenticated: false
    }
  },
  created(){
    this.fetchUser()
  },
  methods:{
    fetchUser(){
      this.currentUser = {...this.currentUser,...dummyUser.currentUser}
      this.isAuthenticated = dummyUser.isAuthenticated
    }
  }
}
</script>

