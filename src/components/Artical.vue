<template>
  <article class="article">
    <a
      v-if="isMainPage"
      class="article__link link-hover"
      :href="`/new/${article.id}`"
      @click="handleArticleClick"
    >
      {{ article.title || "" }}
    </a>
    <a v-else class="article__link link-hover" :href="url" target="_blank">
      {{ article.title || "" }}
    </a>

    <div v-if="!isMainPage" class="article__text">{{ articleText }}</div>
    <p class="article__info">
      <span v-if="isMainPage" class="article__caption">{{
        `${article.score || 0} point${article.score > 1 ? "s" : ""}`
      }}</span>

      <!-- <span class="article__caption">{{
        `by ${article.by || ""} ${convertDate(time) || ""}`
      }}</span> -->
      <span class="article__caption">{{
        `by ${article.by || ""} ${article.time || ""}`
      }}</span>
      <span
        v-if="isMainPage || commentsNum === 0"
        class="article__caption article__caption_content_comments"
      >
        {{ commentsElementText }}
      </span>
      <button
        v-else
        type="button"
        :class="commentsButtonClass"
        @click="onCommentsButtonClick"
      >
        {{ commentsElementText }}
      </button>
    </p>
  </article>
</template>

<script>
export default {
  name: "Arcticle",
  props: [
    "article",
    "onArticleClick",
    "commentsIsOpen",
    "onCommentsButtonClick",
    "isMainPage",
  ],
  methods: {
    handleArticleClick() {
      this.onArticleClick(this.article);
    },
  },
  data() {
    return {
      articleText:
        this.article.text ||
        "Follow the link in the title to read the full text",
      commentsNum: this.article.kids ? this.article.kids.length : 0,

      commentsButtonClass: `article__caption article__caption_content_comments article__button link-hover ${
        this.commentsIsOpen
          ? "article__button_state-comment_open"
          : "article__button_state-comment_close"
      }`,
    };
  },
  computed: {
    commentsText() {
      return this.commentsNum === 1 ? "comment" : "comments";
    },
    commentsElementText() {
      return (this.commentsNum || "no") + " " + this.commentsText;
    },
  },
};

// const { id, title, text, url, score, by, time, kids } = article;

</script>

<style>
.article__link {
  color: var(--black);
  text-decoration: none;
  font-size: 16px;
  line-height: 1.2;
  font-weight: 700;
  margin: 0;
}

.article__text {
  box-sizing: border-box;
  margin: 5px 0 0;
  font-size: 14px;
  line-height: 1.2;
  font-weight: normal;
  color: var(--black);
  flex-grow: 1;
}

.article__info {
  margin: 5px 0 0;
  display: flex;
}

.article__caption {
  font-size: 12px;
  line-height: 1.2;
  font-weight: normal;
  color: var(--gray);
  box-sizing: border-box;
}

.article__caption:not(:last-child) {
  margin-right: 5px;
}

.article__caption_content_comments {
  padding: 0 0 0 5px;
  border-left: 1px solid var(--gray);
}

.article__button {
  border-top: none;
  border-right: none;
  border-bottom: none;
  background: none;
  cursor: pointer;
  display: flex;
}

.article__button_state-comment_close::before {
  content: " ";
  display: inline-block;
  border-top: 14px solid var(--color-bcg-orange);
  border-left: 7px solid transparent;
  border-right: 7px solid transparent;
  border-bottom: 0;
  height: 0px;
  width: 0px;
  margin-right: 5px;
}

.article__button_state-comment_open::before {
  content: " ";
  display: inline-block;
  border-bottom: 14px solid var(--color-bcg-orange);
  border-left: 7px solid transparent;
  border-right: 7px solid transparent;
  border-top: 0;
  height: 0px;
  width: 0px;
  margin-right: 5px;
}
</style>
