<template>
  <ol class="news__list">
    <li v-for="article of news" :key="article.id">
      <Article
        :article="article"
        :onArticleClick="onArticleClick"
        :isMainPage="true"
      />
    </li>
  </ol>
</template>

<script>
import Article from "./Artical.vue";

export default {
  name: "NewsList",
  props: ["news", "onArticleClick"],
  // data() {
  //   return {};
  // },

  components: {
    Article,
  },
};
</script>

<style>
.news__list {
  margin: 0;
  display: grid;
  grid-row-gap: 7px;
  padding: 0 40px;
  box-sizing: border-box;
}

ol li::marker {
  font-size: 14px;
  line-height: 1.2;
  font-weight: normal;
  color: var(--black);
}
</style>
