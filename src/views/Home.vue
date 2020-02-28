<template>
  <b-container>
    <b-row align-v="center">
      <BookCard v-for="book in displayBooks" :book="book" :key="book.id"/>
    </b-row>
    <b-pagination
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
      first-text="First"
      prev-text="Prev"
      next-text="Next"
      last-text="Last"
      @input="paginate(currentPage)"
    ></b-pagination>
  </b-container>
</template>

<script>
import BookCard from "@/components/BookCard";
export default {
  name: "Home",
  components: {
    BookCard
  },
  data () {
    return {
      books: [],
      displayBooks: [],
      currentPage: 1,
      rows: 1,
      perPage: 3
    };
  },
  methods: {
    async fetchData () {
      const res = await fetch("books.json");
      this.books = await res.json();
      this.displayBooks = this.books.slice(0, 3);
      this.rows = this.books.length;
    },
    paginate (currentPage) {
      const start = (currentPage - 1) * this.perPage;
      this.displayBooks = this.books.slice(start, start+3);
    }
  },
  mounted () {
    this.fetchData();
  }
};
</script>
