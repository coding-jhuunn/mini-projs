<template>
  <div>
    <header>
      <nav>
        <nuxt-link to="/products">Products</nuxt-link>
      </nav>
    </header>
    <div>
      <slot />
    </div>
    <footer>
      <ul>
        <li><nuxt-link to="/">Home</nuxt-link></li>
        <li><nuxt-link to="/about">About</nuxt-link></li>
        <li><nuxt-link to="/products">Products</nuxt-link></li>
      </ul>
    </footer>
  </div>
</template>
