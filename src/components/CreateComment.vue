<template>
  <form @submit.stop.prevent="handleSubmit">
    <div class="form-group mb-4">
      <label for="text">留下評論：</label>
      <textarea v-model="text" class="form-control" rows="3" name="text" />
    </div>
    <div class="d-flex align-items-center justify-content-between">
      <button type="button" class="btn btn-link" @click="$router.back()">
        回上一頁
      </button>
      <button type="submit" class="btn btn-primary mr-0">Submit</button>
    </div>
  </form>
</template>

<script>
import { v4 as uuidv4 } from "uuid"

export default{
  props: {
    restaurantId: {
      type: Number,
      required: true,
    }
  },
  data(){
    return {
      text:''
    }
  },
  methods:{
    handleSubmit(){
      console.log('submit')
      //TODO send POST request to API
      // after server renew Comments data:
      this.$emit('after-create-comment', {
        commentId: uuidv4(), //temporary using random id before connecting API
        restaurantId: this.restaurantId,
        text: this.text
      })
      this.text = "" //empty textarea after user submit
    }
  }
}
</script>
