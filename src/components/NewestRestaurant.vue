<template>
  <div class="card">
    <div class="card-header">Newest Restaurants</div>
    <div class="card-body">
      <div
        v-for="restaurant in restaurants"
        :key="restaurant.id"
      >
        <h4>
          <a href="#">{{ restaurant.name }}</a>
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
import moment from 'moment'

export default {
  filters: {
    fromNow(datetime){
      if(!datetime){
        return '-'
      }

      return moment(datetime).fromNow()
    }
  },
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
