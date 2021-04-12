<template>
  <div>
     <div data-collapse="medium" data-animation="default" data-duration="400" class="nav-bar w-nav">
    <div class="wrapper navbar-2 w-container">
      <div class="logo-area"> <router-link class="nav-logo w-inline-block" to="/"> <img src="assets/images/logo-light.svg" width="106" alt=""></router-link></div>
      <nav role="navigation" class="nav-menu-2 w-nav-menu">
        <router-link class="nav-link w-nav-link" to="/">Home</router-link>
        <router-link class="nav-link w-nav-link" to="/">About</router-link>
        <router-link class="nav-link w-nav-link" to="/">Pricing</router-link>
        <router-link class="nav-link w-nav-link w--current" to="/blog">Blog</router-link>
        <router-link class="nav-link w-nav-link" to="/">Career</router-link>
      
        <div class="nav-cta-button-container"><a href="#" class="nav-link-2 border cta w-nav-link">Contact Us</a></div>
      </nav>
      <div class="menu-button-2 w-nav-button">
        <div class="burger-icon w-icon-nav-menu"></div>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
    name: 'Navbar'
}
</script>

<style>

</style>