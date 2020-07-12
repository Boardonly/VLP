<template>
  <div class="vlp-home">
    <Search />
    <v-cataloge />
  </div>
  <!-- /.vlp-home -->
</template>

<script>
// @ is an alias to /src
import Header from "@/components/Header.vue";
import Search from "@/components/home/Search.vue";
import Cataloge from "@/components/home/Cataloge.vue";

export default {
  name: "Home",
  components: {
    Header,
    Search,
    "v-cataloge": Cataloge
  }
};
</script>
<style lang="scss">
</style>
