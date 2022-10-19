<template>
  <ul class="nav nav-tabs mb-4">
    <li 
      v-for="tab in tabs"
      :key="tab.id"
      class="nav-item"
    >
      <router-link 
        :to="tab.path" 
        class="nav-link"
      > 
        {{ tab.title }}
      </router-link>
    </li>
  </ul>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
  data() {
    return {
      tabs: [
        {
          id: uuidv4(),
          title: "Home",
          path: "/restaurants",
        },
        {
          id: uuidv4(),
          title: "Latest Activity",
          path: "/restaurants/feeds",
        },
        {
          id: uuidv4(),
          title: "TOP 10 Restaurants",
          path: "/restaurants/top",
        },
        {
          id: uuidv4(),
          title: "Top User",
          path: "/users/top",
        },
      ],
    };
  },
};
</script>
