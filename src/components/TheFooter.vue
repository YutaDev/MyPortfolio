<template>
  <footer>
    <div class="container">
      <router-link class="logo-font" :to="{ name: 'home', params: {} }">
        MyPortfolio
      </router-link>
      <span class="attribution">
        とりあえず作ったポートフォリオ
        <a rel="noopener noreferrer" target="blank" href="ブログとかのURL"
          >ブログ</a
        >. Code &amp; design licensed under Yuta Miyano.
      </span>
    </div>
  </footer>
</template>

<script>
export default {
  name: "RwvFooter"
};
</script>
