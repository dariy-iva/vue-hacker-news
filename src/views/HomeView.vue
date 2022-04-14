<template>
  <section class="news">
    <NewsList :news="news" :onArticleClick="onArticleClick" />
    <!-- <RefreshButton
        onRefreshButtonClick={refreshNewsList}
        content="news"
        isLoad={newsIsLoad}
      /> -->
  </section>
</template>

<script>
import NewsList from "../components/NewsList.vue";

export default {
  name: "HomeView",
  props: ["news", "onArticleClick"],
  components: {
    NewsList,
  },
};
</script>

<style>
.news {
  width: 100%;
  display: flex;
  flex-direction: column;
  margin: 0;
  padding: 7px 0;
  position: relative;
}
</style>
