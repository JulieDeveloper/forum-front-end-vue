<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="container py-5">
     <NavTabs />
    <!-- <RestaurantsNavPills />-->

    <div class="row">
      <RestaurantCard
        v-for = "restaurant in restaurants" 
        :key = restaurant.id
        :initial-restaurant = "restaurant"
      />
    </div>

    <!-- <RestaurantPagination /> -->
    
  </div>
</template>

<script>
import NavTabs from '../components/NavTabs.vue'
import RestaurantCard from '../components/RestaurantCard.vue'

const dummyData = {
    "restaurants": [
        {
            "id": 1,
            "name": "Mrs. Hosea McCullough",
            "tel": "1-895-444-3509 x39069",
            "address": "62432 Hayden Underpass",
            "opening_hours": "08:00",
            "description": "Magni odit non sunt nobis cupiditate sint. Nulla u",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=75.49650129089265",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 2,
            "name": "Miss Jammie Ullrich",
            "tel": "(862) 063-6448 x394",
            "address": "5292 Nelda Isle",
            "opening_hours": "08:00",
            "description": "Enim voluptatem qui aut quis sapiente architecto u",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=13.603920763826594",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 3,
            "name": "Katelynn Wehner",
            "tel": "673-474-3282 x458",
            "address": "507 McLaughlin Hills",
            "opening_hours": "08:00",
            "description": "molestiae",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=21.265911550810458",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 4,
            "name": "Caleb Crist",
            "tel": "626-595-2454",
            "address": "25427 Howe Hills",
            "opening_hours": "08:00",
            "description": "Itaque aut eaque velit totam aliquid. Dolore solut",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=38.88628964773388",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 5,
            "name": "Tito Adams",
            "tel": "1-820-305-3814 x77860",
            "address": "8533 Hayes Mission",
            "opening_hours": "08:00",
            "description": "voluptas eum quas",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=28.3888639149676",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 6,
            "name": "Daisha Larkin",
            "tel": "1-010-800-4287",
            "address": "96217 Ledner Walks",
            "opening_hours": "08:00",
            "description": "Ea tempore suscipit voluptatem.\nNihil necessitatib",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=49.9710956323717",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 7,
            "name": "Mr. Annamae Hartmann",
            "tel": "536.708.7768",
            "address": "6014 O'Connell Square",
            "opening_hours": "08:00",
            "description": "Temporibus et corrupti possimus velit culpa. Conse",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=68.30704810863324",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 8,
            "name": "Julia Sporer",
            "tel": "1-777-168-3799",
            "address": "5973 Lucie Ranch",
            "opening_hours": "08:00",
            "description": "similique",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=47.914433664111144",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 9,
            "name": "Katharina Zulauf",
            "tel": "(193) 776-7721 x3456",
            "address": "05067 Wunsch Avenue",
            "opening_hours": "08:00",
            "description": "Ad autem inventore qui est odit totam consequatur.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=91.1039879471454",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        },
        {
            "id": 10,
            "name": "Luella Davis",
            "tel": "994-021-6194 x82970",
            "address": "0582 Lehner Mount",
            "opening_hours": "08:00",
            "description": "Sed quibusdam similique fuga dolor. Qui praesentiu",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=12.453909973417066",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            },
            "isFavorited": false,
            "isLiked": false
        }
    ],
    "categories": [
        {
            "id": 1,
            "name": "中式料理",
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z"
        },
        {
            "id": 2,
            "name": "日本料理",
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z"
        },
        {
            "id": 3,
            "name": "義大利料理",
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z"
        },
        {
            "id": 4,
            "name": "墨西哥料理",
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z"
        },
        {
            "id": 5,
            "name": "素食料理",
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z"
        },
        {
            "id": 6,
            "name": "美式料理",
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z"
        },
        {
            "id": 7,
            "name": "複合式料理",
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z"
        }
    ],
    "categoryId": "",
    "page": 1,
    "totalPage": [
        1,
        2,
        3,
        4,
        5
    ],
    "prev": 1,
    "next": 2
}

export default {
  components: {
    NavTabs,
    RestaurantCard
  },
  data(){
    return {
      restaurants: [],
      categories: [],
      categoryId: -1,
      currentPage: 1,
      totalPage: [],
      previousPage: -1,
      nextPage: -1
    }
  },
  created(){
    this.fetchRestaurants()
  },
  methods:{
    fetchRestaurants(){
      const {
        restaurants, 
        categories, 
        categoryId, 
        page, 
        totalPage,
        prev, 
        next  
      } = dummyData
      this.restaurants = restaurants
      this.categories = categories
      this.categoryId = categoryId
      this.currentPage = page
      this.totalPage = totalPage
      this.previousPage = prev
      this.nextPage = next
    }
  }
}
</script>
