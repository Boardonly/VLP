<template>
  <div class="vlp-catalog">
    <div class="vlp-container--small">
      <h2 class="vlp-catalog__title">Усі видання</h2>
      <div class="vlp-catalog__nav">
        <div class="vlp-catalog__sort">
          <p>сортувати за...</p>
          <select name="sort" id="sort" v-on:change="sortBooks">
            <option value="stock" selected>популярністю</option>
            <option value="lowerPrice">ціною вниз</option>
            <option value="highetPrice">ціною вгору</option>
          </select>
        </div>
        <!-- /.vlp-catalog__sort -->
      </div>
      <div class="vlp-catalog__list">
        <Card v-for="(book, i) in this.books" v-bind:book="book" :key=i />
      </div>
    </div>
    <!-- /.vlp-container -->
    <!-- /.vlp-catalog__list -->
  </div>
</template>


<script>
import Card from "@/components/catalog/Card.vue";

export default {
  name: "Catalog",
  components: {
    Card
  },
  data() {
    return {
      books: null,
      copyBooks: null
    };
  },
  created() {
    fetch("data/books_data.json")
      .then(result => result.json())
      .then(data => {
        this.books = [...data["books-list"]];
        this.copyBooks = [...data["books-list"]];
      });
  },
  methods: {
    sortBooks() {
      let newBooks = [...this.books];
      let oldBooks = [...this.books];
      console.log(oldBooks);
      let select = document.getElementById("sort");
      if (select.value === "lowerPrice") {
        this.books = newBooks.sort((a, b) => a.price - b.price);
      } else if (select.value === "highetPrice") {
        this.books = newBooks.sort((a, b) => b.price - a.price);
      } else if (select.value === "stock") {
        this.books = this.copyBooks;
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.vlp-catalog {
  display: flex;
  text-align: center;

  &__list {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;

    .vlp-card {
      width: 100%;
    }
    @media screen and (min-width: 640px) {
      flex-wrap: wrap;
      flex-direction: row;

      .vlp-card {
        width: calc(50% - 30px);
      }
    }
    @media screen and (min-width: 1024px) {
      .vlp-card {
        width: calc(25% - 30px);
      }
    }
  }
  &__title {
    font: 400 36px/1.1 "Philosopher", sans-serif;
    position: relative;
    &::after {
      content: "";
      height: 1px;
      position: absolute;
      width: 373px;
      left: calc(50% - 373px / 2 + 0.5px);
      top: 46px;
      background: #110601;
    }
  }
}
</style>