<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">TOP 10 Restaurants</h1>

    <hr />
    <div 
      v-for="restaurant in restaurants"
      :key= "restaurant.id"
      class="card mb-3" 
      style="max-width: 540px; margin: auto"
    >
      <div class="row no-gutters">
        <div 
         class="col-md-4"
        >
          <a href="#">
            <img
              class="card-img"
              :src="restaurant.image"
            />
          </a>
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">{{ restaurant.name }}</h5>
            <span class="badge badge-secondary">Saved : {{restaurant.FavoriteCount}}</span>
            <p class="card-text">
              {{ restaurant.description }}
            </p>
            <a href="#" class="btn btn-primary mr-2">Show</a>

            <button
              v-if=" restaurant.isFavorited "
              @click.stop.prevent="deleteFavorite(restaurant.id)"
              type="button" 
              class="btn btn-danger mr-2"
            >
              Remove from Favorite
            </button>
            <button 
              v-else
              @click.stop.prevent="addFavorite(restaurant.id)"
              type="button" 
              class="btn btn-primary"
            >
              Add to Favorite
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";

const dummyData = {
    "restaurants": [
        {
            "id": 50,
            "name": "Johnny Johnson",
            "tel": "731-194-2371 x010",
            "address": "71379 Connie Unions",
            "opening_hours": "08:00",
            "description": "Soluta qui praesentium est enim et deserunt. Vel a",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=68.86545577441343",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 3,
            "FavoritedUsers": [],
            "isFavorited": true,
            "FavoriteCount": 333
        },
        {
            "id": 49,
            "name": "Dasia Lockman",
            "tel": "099-831-3004 x85713",
            "address": "806 Dasia Island",
            "opening_hours": "08:00",
            "description": "cumque reprehenderit dolores",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=43.97142804666141",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 245
        },
        {
            "id": 48,
            "name": "Gay Reichel",
            "tel": "506-647-5895 x317",
            "address": "598 Larkin Mall",
            "opening_hours": "08:00",
            "description": "recusandae placeat ut",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=87.55508872876447",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 1,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 382
        },
        {
            "id": 47,
            "name": "Creola Bergstrom",
            "tel": "(304) 600-3490",
            "address": "102 Corwin Estates",
            "opening_hours": "08:00",
            "description": "perferendis",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=69.51539494696478",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 3,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 291
        },
        {
            "id": 46,
            "name": "Kaylie Carter IV",
            "tel": "(628) 744-6873",
            "address": "2328 Mohamed Place",
            "opening_hours": "08:00",
            "description": "Nihil consequuntur eum error atque.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=4.250656091485316",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 288
        },
        {
            "id": 45,
            "name": "Nathanial Bartoletti",
            "tel": "1-105-729-7710",
            "address": "84596 Tillman Point",
            "opening_hours": "08:00",
            "description": "Et ducimus quae omnis tempore nihil. Dignissimos t",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=44.8783622503874",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 3,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 276
        },
        {
            "id": 44,
            "name": "Ashlee Keeling",
            "tel": "666-359-4229 x583",
            "address": "48934 Aniya Locks",
            "opening_hours": "08:00",
            "description": "magni",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=33.63862853495545",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 4,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 267
        },
        {
            "id": 43,
            "name": "June Boyer",
            "tel": "(578) 353-1600",
            "address": "73386 Stanton Wall",
            "opening_hours": "08:00",
            "description": "Et aspernatur odio voluptatem sed tempora ex tempo",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=25.444727797235544",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 4,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 266
        },
        {
            "id": 42,
            "name": "Garret Green III",
            "tel": "144.609.6000 x727",
            "address": "44189 Zemlak Hills",
            "opening_hours": "08:00",
            "description": "Sed veniam maiores nihil non veniam. Ea est et sit",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=21.498278564245087",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 1,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 259
        },
        {
            "id": 41,
            "name": "Stefan Bayer",
            "tel": "855.626.4758",
            "address": "94781 Zakary Neck",
            "opening_hours": "08:00",
            "description": "Similique rem et quae delectus omnis omnis vitae n",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=71.6705188084112",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 198
        }
    ]
}

export default {
  components: {
    NavTabs,
  },
  data(){
    return {
      restaurants:[],
    }
  },
  created(){
    this.fetchRestaurants()
  },
  methods: {
    fetchRestaurants(){
      const {restaurants} = dummyData
      this.restaurants = restaurants
    },
    addFavorite(id){
      this.restaurants.forEach(restaurant => {
        if(restaurant.id === id){
          return restaurant.isFavorited = true
        }
      })
    },
    deleteFavorite(id){
      this.restaurants.forEach(restaurant => {
        if(restaurant.id === id){
          return restaurant.isFavorited = false
        }
      })
    }
  }
};
</script>
