<template>
  
    <div>
      
      <header>
          <nav>
              <ul class="">
                  <li><NuxtLink to="">Home</NuxtLink> </li>
                  <li><NuxtLink to="/about">About</NuxtLink> </li>
                  <li><NuxtLink to="/todos">Todos</NuxtLink> </li>
              </ul>
          </nav>
      </header>
      <slot />
    </div>
  </template>
  
  <script>
  export default {};
  </script>
  
  <style scoped>
  .router-link-exact-active {
    color: #12b488;
  }
  </style>