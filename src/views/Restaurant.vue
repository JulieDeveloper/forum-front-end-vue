<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="container py-5">
    <RestaurantDetail
      :initial-restaurant = "restaurant"
    />
    <hr>
    <RestaurantComments 
      :restaurant-comments="restaurantComments"
      @after-delete-comment="afterDeleteComment"
    />
    <!-- 新增評論 CreateComment -->
  </div>
</template>

<script>
import RestaurantDetail from '../components/RestaurantDetail.vue'
import RestaurantComments from '../components/RestaurantComments.vue'

const dummyData = {
    "restaurant": {
        "id": 1,
        "name": "Mrs. Hosea McCullough",
        "tel": "1-895-444-3509 x39069",
        "address": "62432 Hayden Underpass",
        "opening_hours": "08:00",
        "description": "Magni odit non sunt nobis cupiditate sint. Nulla unde exercitationem quos aspernatur. Quis ea dolor quis perferendis.\n \rEa sint libero minus placeat. Expedita molestiae qui libero. Quisquam unde recusandae amet ex suscipit. Non accusamus debitis libero. Nobis omnis autem qui architecto consectetur et.\n \rImpedit est officiis qui dolorem. Sed voluptatibus reiciendis harum. Incidunt et nesciunt. Eos ad occaecati necessitatibus ut. Ut officiis consectetur autem alias illo.",
        "image": "https://loremflickr.com/320/240/restaurant,food/?random=75.49650129089265",
        "viewCounts": 1,
        "createdAt": "2022-10-21T11:58:14.000Z",
        "updatedAt": "2022-10-24T22:30:43.853Z",
        "CategoryId": 3,
        "Category": {
            "id": 3,
            "name": "義大利料理",
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z"
        },
        "FavoritedUsers": [],
        "LikedUsers": [],
        "Comments": [
            {
                "id": 101,
                "text": "Totam illum aut qui voluptas eos quo et.",
                "UserId": 3,
                "RestaurantId": 1,
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z",
                "User": {
                    "id": 3,
                    "name": "user2",
                    "email": "user2@example.com",
                    "password": "$2a$10$PGrou.H0NZZLEYaLe2yvYOeL.m7n1CwH8B9iLqSB1SEuCPasKJLBG",
                    "isAdmin": false,
                    "image": null,
                    "createdAt": "2022-10-21T11:58:14.000Z",
                    "updatedAt": "2022-10-21T11:58:14.000Z"
                }
            },
            {
                "id": 51,
                "text": "Reprehenderit veritatis ut aut nisi.",
                "UserId": 2,
                "RestaurantId": 1,
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z",
                "User": {
                    "id": 2,
                    "name": "user1",
                    "email": "user1@example.com",
                    "password": "$2a$10$qMd2WAX5KCw.Z.KEENPxhuIsgXKfRh52IoOSBI6Hb1eG0hcCN2bZu",
                    "isAdmin": false,
                    "image": null,
                    "createdAt": "2022-10-21T11:58:14.000Z",
                    "updatedAt": "2022-10-21T11:58:14.000Z"
                }
            },
            {
                "id": 1,
                "text": "Ut officiis ut placeat delectus nihil voluptas.",
                "UserId": 1,
                "RestaurantId": 1,
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z",
                "User": {
                    "id": 1,
                    "name": "root",
                    "email": "root@example.com",
                    "password": "$2a$10$hU92lxKGfm.NRehuKL00G.f4Ira6jwr5dbAUFNQulqiK18EGhMdUm",
                    "isAdmin": true,
                    "image": null,
                    "createdAt": "2022-10-21T11:58:14.000Z",
                    "updatedAt": "2022-10-21T11:58:14.000Z"
                }
            }
        ]
    },
    "isFavorited": false,
    "isLiked": false
}
export default {
  components:{
    RestaurantDetail,
    RestaurantComments,
  },
  data() {
    return {
      restaurant: {
        id: -1,
        name: '',
        categoryName: '',
        image: '',
        openingHours: '',
        tel: '',
        address: '',
        description: '',
        isFavorited: false,
        isLiked: false
      },
      restaurantComments: []
    }
  },
  created(){
    const { id:restaurantId } = this.$route.params
    this.fetchRestaurant(restaurantId)
  },
  methods: {
    fetchRestaurant (restaurantId) {
      console.log('fetchRestaurant id: ', restaurantId)

      this.restaurant = {
        id: dummyData.restaurant.id,
        name: dummyData.restaurant.name,
        categoryName: dummyData.restaurant.Category.name,
        image: dummyData.restaurant.image,
        openingHours: dummyData.restaurant.opening_hours,
        tel: dummyData.restaurant.tel,
        address: dummyData.restaurant.address,
        description: dummyData.restaurant.description,
        isFavorited: dummyData.isFavorited,
        isLiked: dummyData.isLiked,
      }

      this.restaurantComments = dummyData.restaurant.Comments
    },
    afterDeleteComment(commentId){
      this.restaurantComments = this.restaurantComments.filter(comment => comment.id !== commentId)
    }
  }
}
</script>