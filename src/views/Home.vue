<template>
  <div class="vlp-home">
    <Search />
    <v-cataloge />
    <Events />

    <CatalogeMob />
  </div>
  <!-- /.vlp-home -->
</template>


<script>
// @ is an alias to /src
import Header from "@/components/Header.vue";
import Search from "@/components/home/Search.vue";
import Cataloge from "@/components/home/Cataloge.vue";

import Events from "@/components/home/Events.vue";
import Footer from "@/components/Footer.vue";
import CatalogeMob from "@/components/home/CatalogeMob.vue";

export default {
  name: "Home",
  components: {
    Header,
    Search,
    Events,
    Footer,
    "v-cataloge": Cataloge,
    CatalogeMob
  }
};
</script>
<style lang="scss">
</style>
