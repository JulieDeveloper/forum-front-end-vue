<template>
  <div class="container py-5">
    <div>
      <h1>{{ restaurant.name }}</h1>
      <span class="badge badge-secondary mt-1 mb-3">
        {{ restaurant.categoryName }}
      </span>
    </div>
    <hr>
    <ul>
      <li>
        {{ restaurant.commentsLength }} Comments
      </li>
      <li>
        {{ restaurant.viewCounts }} Viewed
      </li>
    </ul>

    <button
      type="button"
      class="btn btn-link"
      @click="$router.back()"
    >
      Back
    </button>
  </div>
</template>

<script>
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
        "updatedAt": "2022-10-24T22:30:43.000Z",
        "CategoryId": 3,
        "Category": {
            "id": 3,
            "name": "義大利料理",
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z"
        },
        "Comments": [
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
            }
        ]
    }
}

export default {
  data() {
    return {
      restaurant: {
        id: -1,
        name: '',
        categoryName: '',
        commentsLength: -1,
        viewCounts: -1
      }
    }
  },
  created(){
    this.fetchRestaurant()
  },
  methods: {
    fetchRestaurant(){
      this.restaurant ={
        id: dummyData.restaurant.id,
        name: dummyData.restaurant.name,
        categoryName: dummyData.restaurant.Category.name,
        commentsLength: dummyData.restaurant.Comments.length,
        viewCounts: dummyData.restaurant.viewCounts
      }
    }
  }
}
</script>
