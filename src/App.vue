<template>
  <nav class="navbar navbar-expand-lg">
    <div class="m-auto d-flex">
      <router-link to="/" class="nav-link">Home</router-link>
      <router-link to="/about" class="nav-link">About</router-link>
      <router-link to="/contact" class="nav-link">Contact</router-link>
    </div>
  </nav>
  <router-view v-slot="{ Component }">
    <transition name="route" mode="out-in"> 
      <component :is="Component"></component> 
      </transition>
  </router-view>
</template>

<style>

.route-enter-from{
  opacity: 0;
  transform: translateX(100px);
}
.route-leave-to{
  opacity: 0;
  transform: translateX(-100px);
}
.route-enter-active {
  transition: all 0.3s ease-out;
}

.route-leave-active {
  transition: all 0.3s ease-in;
}
</style>
