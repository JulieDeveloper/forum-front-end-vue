<template>
  <nav aria-label="Page navigation example">
    <ul class="pagination">
      <!-- Prev Page -->
      <li 
        v-show="previousPage"
        :class="['page-item', {disabled: currentPage === 1}]"
      >
        <router-link
          :to="{
            name: 'restaurants',
            query: {categoryId, page: previousPage}
          }"
          class="page-link"
          aria-label="Previous"
        >
          <span aria-hidden="true">&laquo;</span>
        </router-link>
        <a class="page-link" aria-label="Previous" href="#">
          
        </a>
      </li>

      <!-- Pages -->
      <li 
        v-for="page in totalPage"
        :key="page"
        :class="['page-item',{ active: currentPage === page }]"
      >
        <router-link
          class="page-link"
          :to= "{name: 'restaurants', query: { categoryId, page }}"
        >
          {{ page }}
        </router-link>
      </li>

      <!-- Next Page -->
      <li
        v-show="nextPage"
        :class="['page-item', { disabled: currentPage === totalPage.length }]"
      >
        <router-link
          class="page-link"
          :to="{ name: 'restaurants', query: { categoryId, page: nextPage } }"
          aria-label="Next"
        >
          <span aria-hidden="true">&raquo;</span>
        </router-link>
      </li>
    </ul>
  </nav>
</template>

<script>

export default {
  props: {
    categoryId: {
      type: [String, Number],
      default: ''
    },
    currentPage: {
      type: Number,
      default: 1
    },
    totalPage: {
      type: Array,
      required: true
    },
    previousPage: {
      type: Number,
      required: true
    },
    nextPage: {
      type: Number,
      required: true
    }
  }
}
</script>
