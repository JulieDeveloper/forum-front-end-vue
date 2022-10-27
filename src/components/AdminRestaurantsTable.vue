<template>
  <table class="table">
    <thead class="thead-dark">
      <tr>
        <th scope="col">#</th>
        <th scope="col">Category</th>
        <th scope="col">Name</th>
        <th scope="col" width="300">Control</th>
      </tr>
    </thead>
    <tbody>
      <tr 
        v-for="restaurant in restaurants" 
        :key="restaurant.id"
      >
        <th scope="row">
          {{ restaurant.id }}
        </th>
        <td>
          {{ restaurant.Category ? restaurant.Category.name : "Uncategorized" }}
        </td>
        <td>
          {{ restaurant.name }}
        </td>
        <td class="d-flex justify-content-between">
          <router-link :to=" { name: 'admin-restaurant', params: {id: restaurant.id} }" class="btn btn-link">Show</router-link>

          <a href="#" class="btn btn-link">Edit</a>

          <button 
            type="button" 
            class="btn btn-link" 
            @click.stop.prevent="deleteRestaurant(restaurant.id)"
          >
            Delete
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
const dummyData = {
    "restaurants": [
        {
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
            }
        },
        {
            "id": 2,
            "name": "Miss Jammie Ullrich",
            "tel": "(862) 063-6448 x394",
            "address": "5292 Nelda Isle",
            "opening_hours": "08:00",
            "description": "Enim voluptatem qui aut quis sapiente architecto ullam eius qui. Omnis eos deleniti. Autem tenetur cumque tempora sint facilis ipsum id.\n \rSaepe culpa corrupti voluptatem. Ea incidunt commodi porro odio ut sint a occaecati. Velit recusandae amet eveniet illum aliquid perferendis. Ipsa similique temporibus inventore.\n \rDolores sit dolorem dolore soluta qui id delectus. Qui commodi consequuntur et quia. Fugiat ut repellendus quam adipisci omnis culpa reiciendis rerum.",
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
            }
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
            }
        },
        {
            "id": 4,
            "name": "Caleb Crist",
            "tel": "626-595-2454",
            "address": "25427 Howe Hills",
            "opening_hours": "08:00",
            "description": "Itaque aut eaque velit totam aliquid. Dolore soluta ipsum assumenda. Aut eius dolor delectus qui assumenda vel. Omnis esse et alias assumenda omnis et libero. Enim ipsam accusantium beatae sit quod vitae sit.\n \rNihil culpa iste et dolorem aliquid. Optio error necessitatibus dolorum nihil quidem sunt porro ullam. Consequuntur voluptas debitis aut in aut repudiandae sit eius vero.\n \rQui omnis quo ea culpa rerum vel consectetur. Non quas vel. Reprehenderit reiciendis suscipit tempora nam et sunt nesciunt. Ut cum rerum molestias ex ut porro. Facere nulla eaque veritatis rerum aspernatur quas.",
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
            }
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
            }
        },
        {
            "id": 6,
            "name": "Daisha Larkin",
            "tel": "1-010-800-4287",
            "address": "96217 Ledner Walks",
            "opening_hours": "08:00",
            "description": "Ea tempore suscipit voluptatem.\nNihil necessitatibus qui dolores est praesentium.\nAut commodi quisquam sunt.\nCulpa ut beatae a esse officiis.\nSunt mollitia temporibus animi fugit omnis.",
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
            }
        },
        {
            "id": 7,
            "name": "Mr. Annamae Hartmann",
            "tel": "536.708.7768",
            "address": "6014 O'Connell Square",
            "opening_hours": "08:00",
            "description": "Temporibus et corrupti possimus velit culpa. Consequatur eos fugiat nemo iure. Praesentium voluptatibus quia officia officia ab consequatur sit. Velit consectetur omnis enim occaecati in pariatur non laboriosam est. Repudiandae omnis incidunt et aut excepturi et repudiandae.\n \rEt architecto totam iusto sunt veritatis doloremque. Rem hic dignissimos officiis suscipit aut cum iure alias. Aut recusandae animi et qui illo sapiente explicabo. Ipsam corporis id pariatur ut et autem omnis quae vero. Cupiditate distinctio ea quae et libero id. Dolor iste rerum quia architecto maxime mollitia.\n \rVoluptatem non unde omnis aperiam quidem. Dolorem sunt doloribus. Quia quidem praesentium voluptatem.",
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
            }
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
            }
        },
        {
            "id": 9,
            "name": "Katharina Zulauf",
            "tel": "(193) 776-7721 x3456",
            "address": "05067 Wunsch Avenue",
            "opening_hours": "08:00",
            "description": "Ad autem inventore qui est odit totam consequatur.\nQui animi incidunt.\nCulpa dicta ea culpa.",
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
            }
        },
        {
            "id": 10,
            "name": "Luella Davis",
            "tel": "994-021-6194 x82970",
            "address": "0582 Lehner Mount",
            "opening_hours": "08:00",
            "description": "Sed quibusdam similique fuga dolor. Qui praesentium asperiores exercitationem. Molestiae corrupti quibusdam minima et sed facere. Architecto amet molestiae in qui. Nostrum sed minus aliquid est provident reprehenderit.",
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
            }
        },
        {
            "id": 11,
            "name": "Augustine Volkman",
            "tel": "453.083.3016",
            "address": "896 Micaela Harbors",
            "opening_hours": "08:00",
            "description": "Voluptate eos quo repellendus amet et ducimus voluptatibus. Cumque molestiae dolorem aut ipsum qui quam. Voluptatibus fugiat nobis voluptas necessitatibus officiis officia accusantium tenetur qui.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=72.62630798183972",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 12,
            "name": "Arnulfo Vandervort",
            "tel": "718.820.6951 x802",
            "address": "167 Kemmer Lake",
            "opening_hours": "08:00",
            "description": "Quibusdam quibusdam officiis est vero ea voluptate nam nemo. Dolore qui facere facere ducimus sed fugiat. Ut architecto ducimus vel dolor perspiciatis.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=25.962203735769496",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 13,
            "name": "Kenny Stanton",
            "tel": "422.213.6820 x61707",
            "address": "24722 Greenholt Rue",
            "opening_hours": "08:00",
            "description": "Sunt enim et perferendis suscipit modi sunt quis ut. Pariatur cupiditate vel molestiae occaecati maxime. Repellat ut et rerum et aliquam iste. Voluptas ut et dolores eligendi.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=26.616456908471164",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 14,
            "name": "Mr. Elwyn Simonis",
            "tel": "(385) 301-0422 x62152",
            "address": "2888 Kirk Shoals",
            "opening_hours": "08:00",
            "description": "Fugiat debitis dolores non perspiciatis est aperiam non esse deserunt. Odit nihil eaque in non est. Rerum accusamus quo aut sint at sunt quisquam.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=54.12405144136825",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 15,
            "name": "Brandi Gulgowski",
            "tel": "522-715-7301 x820",
            "address": "9190 Stokes Inlet",
            "opening_hours": "08:00",
            "description": "dolor dignissimos officiis",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=76.79325989749364",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 16,
            "name": "Kellie Feil",
            "tel": "1-314-088-3988 x51272",
            "address": "5549 Wolf Fall",
            "opening_hours": "08:00",
            "description": "Veniam pariatur consequatur vel et est in ut.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=64.76295230046418",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 17,
            "name": "Jeff Will",
            "tel": "1-468-268-6806",
            "address": "20882 Aileen Keys",
            "opening_hours": "08:00",
            "description": "quisquam accusamus velit",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=24.849968707567903",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 18,
            "name": "Royce Klocko",
            "tel": "718.160.5992 x1296",
            "address": "17177 Abernathy Parkway",
            "opening_hours": "08:00",
            "description": "optio",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=40.8783461583937",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 19,
            "name": "Madalyn Daugherty",
            "tel": "1-035-262-6163 x4730",
            "address": "7695 McKenzie Gardens",
            "opening_hours": "08:00",
            "description": "et debitis voluptatem",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=12.235760456500056",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 20,
            "name": "Lauren Mohr",
            "tel": "(276) 815-3616 x20639",
            "address": "6151 Berge Stream",
            "opening_hours": "08:00",
            "description": "Ut porro mollitia molestiae est fugit ullam pariatur.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=31.455676378846874",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 21,
            "name": "Pete Adams",
            "tel": "184.519.3571 x3339",
            "address": "34061 Thea Point",
            "opening_hours": "08:00",
            "description": "Ea aut et et et iste. Sit sapiente consequuntur quos sed quisquam beatae. Iure explicabo impedit eligendi temporibus autem consectetur consequuntur quam.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=62.24551404159362",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 22,
            "name": "Elody Heidenreich",
            "tel": "846-146-3791",
            "address": "569 Britney Stream",
            "opening_hours": "08:00",
            "description": "Fuga tenetur ullam quasi nesciunt reprehenderit porro quo praesentium. Dignissimos itaque tenetur ut aperiam accusamus ducimus iste qui quia. Sunt in nihil. Sit quo voluptatum vitae optio placeat et. Illum et nihil.\n \rSapiente ut fuga dolor doloremque tempora ullam. Quibusdam qui veritatis placeat a totam molestias voluptatem occaecati odit. Ex odio soluta dignissimos laborum itaque fugiat. Beatae ut officiis. Sit et nesciunt magni distinctio magni.\n \rEt repellat suscipit tempore. Sapiente veniam quia. Ipsum quod sunt quisquam atque blanditiis repellendus vitae sunt occaecati. Consequatur ipsam natus enim eum ea corporis sapiente aut. Eos neque iste ipsa voluptas quia minima quas. Omnis sed quidem magni.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=79.15226945354495",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 23,
            "name": "Carroll Kiehn IV",
            "tel": "091-322-2939",
            "address": "3502 Dayne Summit",
            "opening_hours": "08:00",
            "description": "Iure omnis repellat. Nesciunt rerum temporibus praesentium pariatur. Sit incidunt est adipisci impedit non placeat molestiae nam quae. Laborum soluta commodi sit vel possimus fuga assumenda est sit. Magni vero molestiae optio quia id aperiam voluptas mollitia.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=45.49965114618744",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 24,
            "name": "Maurine Stokes",
            "tel": "1-811-737-8951 x4109",
            "address": "90734 Franecki Key",
            "opening_hours": "08:00",
            "description": "quisquam",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=78.07779969573801",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 25,
            "name": "Luigi Bernier",
            "tel": "(206) 346-9035",
            "address": "941 Parker Coves",
            "opening_hours": "08:00",
            "description": "Qui esse doloremque nobis quaerat.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=66.32638852392535",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 26,
            "name": "Gerson Ratke",
            "tel": "(721) 837-3779",
            "address": "268 Turner Orchard",
            "opening_hours": "08:00",
            "description": "nesciunt voluptates quis",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=90.02857901372639",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 27,
            "name": "Jamil Waelchi",
            "tel": "(788) 449-2362",
            "address": "410 Opal Isle",
            "opening_hours": "08:00",
            "description": "Repellat iusto minima.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=44.55685777598306",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 28,
            "name": "Abbey Schmitt",
            "tel": "1-554-524-6887 x644",
            "address": "847 Torphy Mountains",
            "opening_hours": "08:00",
            "description": "Et labore aut possimus perferendis voluptatem deserunt qui ut ducimus.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=58.041398069626496",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 29,
            "name": "Hank Davis",
            "tel": "000.606.2936",
            "address": "9607 O'Connell Cliff",
            "opening_hours": "08:00",
            "description": "Qui sit est nam aliquid magni ab ut asperiores doloribus.\nDistinctio odit dolor fugiat.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=19.594647376940145",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 30,
            "name": "Laurianne Konopelski",
            "tel": "075.470.5620",
            "address": "517 O'Conner Station",
            "opening_hours": "08:00",
            "description": "Est commodi et voluptatibus voluptates eum.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=24.842482931513743",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 31,
            "name": "Miss Pattie Stark",
            "tel": "1-490-190-0015 x34281",
            "address": "398 Presley Viaduct",
            "opening_hours": "08:00",
            "description": "Natus expedita maiores nulla sit laudantium qui quas aut.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=19.861381134042944",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 32,
            "name": "Myrl Rolfson",
            "tel": "1-379-120-8951",
            "address": "1508 Monahan Drive",
            "opening_hours": "08:00",
            "description": "Quas tempore quia quis iste explicabo sapiente qui voluptas.\nAb qui ut sunt voluptates qui necessitatibus debitis numquam.\nOdit laborum iusto blanditiis quam voluptatem.\nEst qui possimus neque ut.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=42.59279635912987",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 33,
            "name": "Regan Goldner",
            "tel": "349.274.1670 x13507",
            "address": "5161 Pacocha Port",
            "opening_hours": "08:00",
            "description": "Explicabo voluptatem omnis.\nCorrupti aut accusamus optio saepe aut sunt.\nSapiente quae quibusdam quae distinctio quo qui.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=85.06929239238457",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 34,
            "name": "Lisette Corkery",
            "tel": "1-645-066-4710",
            "address": "133 Carlos Lock",
            "opening_hours": "08:00",
            "description": "Eius animi voluptas sunt sunt. Ratione sed veritatis non quod ipsum quas consectetur ea. Sed dolor ad doloribus enim sunt voluptates libero sed similique. Nulla voluptatem et. Rerum voluptatem ipsa totam quia cupiditate. Ut nesciunt velit ipsum est eum minus qui distinctio dolore.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=72.73026895935402",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 35,
            "name": "Dr. Willy Powlowski",
            "tel": "(554) 402-8842",
            "address": "7042 Nicholas Falls",
            "opening_hours": "08:00",
            "description": "Aut quis molestias pariatur nihil dolorum voluptatum magnam enim quod. Placeat harum provident ratione tenetur quidem magni ut officiis. Et consequatur harum saepe vero. Fuga sequi aut quia nisi eum aperiam.\n \rAut quos ut at ipsam. Impedit vero incidunt quam voluptas at iste. Unde consequuntur porro iure adipisci dolor unde cum iste. Expedita omnis doloremque et soluta.\n \rDucimus facilis dolor ipsa. Totam porro enim aspernatur ducimus. Quibusdam corrupti odio ducimus enim. Sed eaque qui reiciendis nostrum. Vel labore nesciunt accusantium similique est.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=28.132134327386062",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 36,
            "name": "Edwardo Heidenreich",
            "tel": "1-101-312-2343",
            "address": "370 Jonas Springs",
            "opening_hours": "08:00",
            "description": "dicta vitae delectus",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=87.43656642642077",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 37,
            "name": "Glen Runolfsson",
            "tel": "135-556-7944",
            "address": "710 Kasandra Causeway",
            "opening_hours": "08:00",
            "description": "Rem officia nobis excepturi reprehenderit. Omnis asperiores consequatur dolorem id sit ut dolorem aut minus. Tempora non similique ut explicabo quia quos minus. Ab blanditiis eveniet atque doloremque corporis aliquam et nihil.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=99.81085225934304",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 38,
            "name": "Dessie Blick",
            "tel": "688-622-2565 x753",
            "address": "271 Janae Branch",
            "opening_hours": "08:00",
            "description": "Perspiciatis aut rerum sint neque vel. Voluptatem accusamus quaerat et est. Exercitationem et nostrum distinctio itaque voluptatem.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=6.955207565052146",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 39,
            "name": "Barbara Schmeler",
            "tel": "(959) 101-9589 x590",
            "address": "89761 Treutel Fall",
            "opening_hours": "08:00",
            "description": "Perspiciatis sit perferendis consequuntur qui dicta et porro.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=71.1276760290718",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 40,
            "name": "Ward Gislason V",
            "tel": "234-175-3654",
            "address": "100 Swaniawski Flat",
            "opening_hours": "08:00",
            "description": "Dolorum repudiandae sapiente in nostrum labore repellendus fuga. Optio dolores consequuntur. Officiis quis magni est dolor quo autem illum ea. Pariatur aliquam deleniti vel excepturi sed animi possimus. Qui qui nesciunt rerum laboriosam quia reprehenderit quod error.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=37.06526267865162",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 41,
            "name": "Stefan Bayer",
            "tel": "855.626.4758",
            "address": "94781 Zakary Neck",
            "opening_hours": "08:00",
            "description": "Similique rem et quae delectus omnis omnis vitae non veritatis. Ut quia dolor maiores ipsa. Qui accusamus molestiae aliquam facere incidunt. Ipsa earum quia quasi consectetur ad quibusdam quasi vitae at. Dignissimos animi ad quisquam debitis laborum. Dolore ullam ut nihil est facilis itaque ad non et.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=71.6705188084112",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 42,
            "name": "Garret Green III",
            "tel": "144.609.6000 x727",
            "address": "44189 Zemlak Hills",
            "opening_hours": "08:00",
            "description": "Sed veniam maiores nihil non veniam. Ea est et sit omnis temporibus. Ea autem voluptas consequatur.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=21.498278564245087",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 43,
            "name": "June Boyer",
            "tel": "(578) 353-1600",
            "address": "73386 Stanton Wall",
            "opening_hours": "08:00",
            "description": "Et aspernatur odio voluptatem sed tempora ex tempora eum.\nDucimus natus voluptatum aut laudantium est quasi sed aliquam qui.\nReprehenderit repudiandae et quasi distinctio.\nSed sint impedit aliquid porro pariatur.\nQuas doloribus quidem aut necessitatibus commodi praesentium consequatur tempore.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=25.444727797235544",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
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
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 45,
            "name": "Nathanial Bartoletti",
            "tel": "1-105-729-7710",
            "address": "84596 Tillman Point",
            "opening_hours": "08:00",
            "description": "Et ducimus quae omnis tempore nihil. Dignissimos tempore ut blanditiis sequi. Quis quia ipsum recusandae doloremque.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=44.8783622503874",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
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
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
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
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
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
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
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
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        },
        {
            "id": 50,
            "name": "Johnny Johnson",
            "tel": "731-194-2371 x010",
            "address": "71379 Connie Unions",
            "opening_hours": "08:00",
            "description": "Soluta qui praesentium est enim et deserunt. Vel adipisci libero rerum itaque in quidem. Incidunt quia vero ratione asperiores dolore. Dolorem neque consequatur ea. Corrupti nobis eligendi vitae.\n \rIn a corrupti qui. Fugiat magnam autem veritatis error velit corrupti est sed. Ab eveniet accusamus illo beatae voluptas perspiciatis quae dicta aut. Occaecati suscipit aut deserunt sint ab harum consectetur. Est consequatur animi eum unde cupiditate.\n \rDolor unde natus aut iure eius aut qui. Doloribus fugiat harum voluptas consequuntur quia quis eos unde. Praesentium ut ut sit et voluptas dolorum vitae.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=68.86545577441343",
            "viewCounts": 0,
            "createdAt": "2022-10-21T11:58:14.000Z",
            "updatedAt": "2022-10-21T11:58:14.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-10-21T11:58:14.000Z",
                "updatedAt": "2022-10-21T11:58:14.000Z"
            }
        }
    ]

};

export default {
  data() {
    return {
      restaurants: [],
    };
  },
  created() {
    this.fetchRestaurants();
  },
  methods: {
    fetchRestaurants() {
      this.restaurants = dummyData.restaurants;
    },
    deleteRestaurant(restaurantId){
      this.restaurants = this.restaurants.filter(restaurant => restaurant.id !== restaurantId)
    }
  },
};
</script>
