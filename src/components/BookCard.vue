<template>
  <div>
    <b-col>
      <b-card
        :title="book.title"
        :img-src="book.imageUrl"
        img-alt="capa livro"
        img-top
        tag="article"
        style="max-width:20rem"
        class="mb-2">
        <b-card-text>
          {{ book.description }}
        </b-card-text>
        <b-button variant="primary">Detalhes</b-button>
      </b-card>
    </b-col>
  </div>
</template>

<script>
export default {
  props: {
    book: Object
  }
}
</script>

<style>
 .card-img-top {
   height: 200px;
   object-fit: cover;
 }
</style>
