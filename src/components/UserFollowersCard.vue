<template>
  <div class="card">
    <div class="card-header">
      <strong>{{ followers.length }}</strong> followers
    </div>
    <div class="card-body">
      <router-link 
        v-for="follower in followers"
        :key="follower.id"
        :to="{ name: 'user',params: { id: follower.id} }"
      >
        <img :src="follower.image" width="60" height="60" class="avatar">
      </router-link>
    </div>
  </div>
</template>
<script>
  export default{
    props:{
      followers:{
        type: Object,
        required: true
      },
    }
  }
</script>