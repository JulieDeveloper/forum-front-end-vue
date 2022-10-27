<template>
  <div class="card mb-3">
    <div class="row no-gutters">
      <div class="col-md-4">
        <img :src="image" width="300px" height="300px">
      </div>
      <div class="col-md-8">
        <div class="card-body">
          <h5 class="card-title">{{ name }}</h5>
          <p class="card-text">
            {{ email }}
          </p>
          <ul class="list-unstyled list-inline">
            <li><strong>{{ commentsNum }}</strong> Comments</li>
            <li><strong>{{ favoritedRestaurantsNum }}</strong> Favorited Restaurants</li>
            <li><strong>{{ followingsNum }}</strong> followings</li>
            <li><strong>{{ followersNum }}</strong> followers</li>
          </ul>
          <p>
            <a href="/users/2/edit"><button type="submit" class="btn btn-primary">edit</button></a>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  export default{
    props:{
      name:{
        type: String,
        required: true
      },
      image:{
        type: String,
        required: true,
      },
      email:{
        type: String,
        required: true
      },
      followingsNum:{
        type: Number,
        required: true,
      },
      followersNum:{
        type: Number,
        required: true,
      },
      commentsNum:{
        type: Number,
        required: true,
      },
      favoritedRestaurantsNum:{
        type: Number,
        required: true,
      },
    }
  }
</script>