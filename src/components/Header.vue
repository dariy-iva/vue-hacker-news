<template>
  <header class="header">
    <nav class="header__menu">
      <a href="/" class="header__logo link-hover">
        <img src="../assets/logo.svg" alt="логотип" class="header__img" />
        <h1 class="header__title">Hacker News</h1>
      </a>
    </nav>
  </header>
</template>

<style>
.header {
  width: 100%;
  margin: 0 auto;
  padding: 2px;
  box-sizing: border-box;
  line-height: 0;
  background-color: var(--color-bcg-orange);
  display: flex;
  align-items: center;
}

.header__logo {
  display: flex;
  text-decoration: none;
}

.header__title {
  margin: 0 0 0 4px;
  color: var(--black);
  font-size: 15px;
  line-height: normal;
  font-weight: 700;
}

.header__img {
  width: 20px;
  height: 20px;
}
</style>
