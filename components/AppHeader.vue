<template>
  <header role="banner" class="app-header">
    <a href='/'>De Voorhoede</a>
    <nav>
      <h2 class="a11y-sr-only">Site menu</h2>
      ...
    </nav>
  </header>
</template>

<style>
  @import '~assets/variables.css';

  .app-header {
    background-color: var(--brand-yellow);
    color: var(--brand-blue);
    display: flex;
    justify-content: space-between;
    font-weight: 300;
    padding: 0 1em;
  }

  .app-header__list {
    display: inline-block;
    margin: 0;
    padding: 0;
  }

  .app-header__item {
    display: inline-block;
  }

  .is-active {
    font-weight: bold;
  }

  .app-header__link {
    text-decoration: none;
    padding: 1em 0.5em;
    display: block;
  }
</style>
