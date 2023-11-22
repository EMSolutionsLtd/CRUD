<script>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">

      <nav class="navbar navbar-expand-lg bg-dark navbar-dark">
        <div class="container">
          <RouterLink class="navbar-brand" active-class="active-link" exact-active-class="exact-active-link" to="/">CRUD</RouterLink>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav ms-auto mb-2 mb-lg-0">

              <li class="nav-item">
                <RouterLink class="nav-link" active-class="active-link" exact-active-class="exact-active-link" to="/">Home</RouterLink>
              </li>
              <li class="nav-item">
                <RouterLink class="nav-link" active-class="active-link" exact-active-class="exact-active-link" to="/about">About Us</RouterLink>
              </li>
              <li class="nav-item">
                <RouterLink class="nav-link" active-class="active-link" exact-active-class="exact-active-link" to="/students">Students</RouterLink>
              </li>
              
            </ul>            
          </div>
        </div>
      </nav>
      
    </div>
  </header>

  <!-- Content -->
  <!-- router/index.js calling -->
  <RouterView /> 

</template>

<style scoped>
a.active-link {
  color: #fff;
}
</style>
