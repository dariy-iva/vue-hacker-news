<template>
  <div id="app">
    <Header />
    <router-view :news="news" :onArticleClick="''"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";

export default {
  name: "app",
  data() {
    return {
      news: [
        {
          id: 1,
          title: "Article 1",
          text: "Article text",
          url: "Article url",
          score: 5,
          by: "Me",
          time: 112263,
          kids: [],
        },
        {
          id: 2,
          title: "Article 2",
          text: "Article text",
          url: "Article url",
          score: 10,
          by: "Me",
          time: 112264,
          kids: [],
        },
        {
          id: 3,
          title: "Article 3",
          text: "Article text",
          url: "Article url",
          score: 1,
          by: "Me",
          time: 112265,
          kids: [],
        },
      ],
    };
  },
  components: {
    Header,
  },
};
</script>

<style>
@import url(./vendor/normalize.css);
@import url(./vendor/fonts/Verdana/verdana.css);

@keyframes loading {
  from {
    transform: rotate(0);
  }
  to {
    transform: rotate(360deg);
  }
}

body {
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}

#app {
  font-family: "Verdana", Arial, sans-serif;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  -webkit-text-size-adjust: 100%;
  -ms-text-size-adjust: 100%;
  -moz-text-size-adjust: 100%;
  width: 100%;
  min-width: 320px;
  max-width: 1280px;
  min-height: 100vh;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  box-sizing: border-box;
  --black: #000;
  --white: #fff;
  --gray: #828282;
  --color-bcg-gray: rgb(246, 246, 239);
  --color-bcg-orange: rgb(255, 102, 0);
  background-color: var(--color-bcg-gray);
}

.link-hover {
  transition: opacity 0.3s;
}

.link-hover:hover {
  opacity: 0.6;
}
</style>
