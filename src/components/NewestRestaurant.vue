<template>
  <div class="card">
    <div class="card-header">Newest Restaurants</div>
    <div class="card-body">
      <div
        v-for="restaurant in restaurants"
        :key="restaurant.id"
      >
        <h4>
          <router-link
            :to="{ name:'restaurant', params:{id: restaurantId} }"
          >
            {{ restaurant.name }}
          </router-link>
          <small>
            {{ restaurant.Category? restaurant.Category.name : 'uncategorized'}}
          </small>
        </h4>
        <p>
          {{ restaurant.description }}
        </p>
        {{ restaurant.createdAt | fromNow }}
        <hr />
      </div>
    </div>
  </div>
</template>

<script>
import { fromNowFilter } from '../utils/mixins'

export default {
  mixins:[fromNowFilter],
  props: {
    restaurants:{
      type: Array,
      required: true, 
    }
  }
}
</script>


<style scoped>
small {
  font-size: 10px;
}
</style>
