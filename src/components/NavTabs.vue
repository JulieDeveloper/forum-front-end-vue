<template>
  <ul class="nav nav-tabs mb-4">
    <li class="nav-item">
      <router-link to="/restaurants" class="nav-link"> 
       Home 
      </router-link>
    </li>
    <li class="nav-item">
      <router-link to="/restaurants/feeds" class="nav-link">
        Latest Activity
      </router-link>
    </li>
    <li class="nav-item">
      <router-link to="/restaurants/top" class="nav-link"> 
        TOP 10 Restaurants
      </router-link>
    </li>
    <li class="nav-item">
      <router-link to="/users/top" class="nav-link">
        Top User
      </router-link>
    </li>
  </ul>
</template>