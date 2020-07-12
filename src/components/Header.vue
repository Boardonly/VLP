
<template>
  <div class="vlp-menu">
    <div class="vlp-menu__logo">
      <svg width="99" height="88" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M0 88l22-73h17l23 73H39l-8-42-9 42H0z" fill="#F9D61C" />
        <path
          d="M63.46 24.6l2.01-1 17.01 51.67L99 65 76 0 39 15l23 73 15.05-9.36 3.31-2.05-16.9-51.99z"
          fill="#110601"
        />
      </svg>
    </div>
    <!-- /.vlp-menu__logo -->
    <nav class="vlp-nav">
      <router-link to="/">Home</router-link>
      <router-link to="/catalog">Catalog</router-link>
      <router-link to="/contacts">Contacts</router-link>
    </nav>
  </div>
  <!-- /.vlp-menu -->
</template>

<script>
export default {
  name: "Header"
};
</script>

<style>
</style>