<template>
  <div class="vlp-new">
    <div class="vlp-continer">
      <h2 class="vlp-new__title">{{main.title}}</h2>
      <div class="vlp-new__slider">
        <VueSlickCarousel v-bind="this.settings" ref="carousel">
          <div class="vlp-card" v-for="(book, i) in this.books" :key="i">
            <img v-bind:src="book.img" :alt="book.author" />
            <div class="vlp-card__content" :style="{backgroundColor: `${book.color}`}">
              <h3 class="vlp-card__title">{{book.name}}</h3>
              <cite class="vlp-card__author">{{book.author}}</cite>
              <p class="vlp-card__price">
                {{book.price}}
                <span>грн</span>
              </p>
            </div>
            <!-- /.vlp-card__content -->
          </div>
        </VueSlickCarousel>
        <button @click="this.showPrev" class="vlp-slider-btn" data-works-left>
          <svg width="32" height="60" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
              d="M.8 31.2L29 59.5c.7.7 1.7.7 2.4 0s.7-1.7 0-2.4L4.4 30 31.5 2.9c.7-.7.7-1.7 0-2.4-.3-.3-.8-.5-1.2-.5-.4 0-.9.2-1.2.5L.8 28.8c-.7.7-.7 1.7 0 2.4z"
              fill="#7F7979"
            />
          </svg>
        </button>
        <button @click="this.showNext" class="vlp-slider-btn" data-works-right>
          <svg width="32" height="60" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
              d="M31.2 28.8L3 .5C2.2-.2 1.2-.2.5.5s-.7 1.7 0 2.4L27.6 30 .5 57.1c-.7.7-.7 1.7 0 2.4.3.3.8.5 1.2.5.4 0 .9-.2 1.2-.5l28.3-28.3c.7-.7.7-1.7 0-2.4z"
              fill="#7F7979"
            />
          </svg>
        </button>
      </div>
      <!-- /.vlp-new__slider -->
    </div>
    <!-- /.vlp-container -->
  </div>
</template>

<script>
import VueSlickCarousel from "vue-slick-carousel";
import "vue-slick-carousel/dist/vue-slick-carousel.css";
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";

export default {
  props: ["books"],
  name: "Slider",
  data() {
    return {
      main: {
        title: "Нове",
        link: "переглянути усе >>",
      },
      settings: {
        infinite: true,
        slidesToShow: 2,
        speed: 500,
        rows: 2,
        slidesPerRow: 1,
        arrows: true,
        dots: true,
      },
    };
  },
  components: {
    VueSlickCarousel,
  },
  methods: {
    showNext() {
      this.$refs.carousel.next();
    },
    showPrev() {
      this.$refs.carousel.prev();
    },
  },
};
</script>

<style scoped lang="scss" scoped>
.vlp-new {
  position: relative;
  .slick-slide {
   &>div + div {
      margin: 15px;
    }
  }
  .vlp-slider-btn {
    position: absolute;
    top: 50%;
    text-decoration: none;
    border: none;
    background: transparent;
    outline: transparent;
    cursor: pointer;
    //  transform: translate(-50%, -50%);
  }
  [data-works-left] {
    left: 0;
  }
  [data-works-right] {
    right: 0;
  }
  &__slider {
    @media screen and (min-width: 640px) {
      padding: 0 90px;
    }
  }
}
.vlp-card {
  display: flex !important;
  text-align: left;
  //   margin: 15px;
  img {
    max-width: 245px;
    width: 100%;
    flex-grow: 1;
  }
  &__content {
    display: flex;
    flex-direction: column;
    max-width: 330px;
    padding: 36px 45px 20px;
  }
  &__title {
    font: 400 22px/1.222 "Forum", sans-serif;
    color: #110601;
    margin: 0;
  }
  &__author {
    font-family: Ubuntu;
    font-weight: 300;
    font-size: 14px;
    line-height: 1.714;
  }
  &__price {
    font-size: 36px;
    margin: 0;
    margin-top: auto;
    span {
      font-size: 18px;
    }
  }
}
</style>