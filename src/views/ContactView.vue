<template>
  <div class="container">
    <h1 class="text-center">Contact</h1>
    <div class="d-flex justify-content-center my-2">
      <transition-group tag="ul" class="row" @before-enter="beforeEnter" @enter="enter" appear>
        <li
          v-for="(icon,index) in icons"
          :data-index = "index"
          :key="icon.name"
          class="card col-5 m-3 "
          style="cursor: pointer; height: 150px"
        >
          <span class="fw-bold bg-light">{{ icon.name }}</span>
          {{ icon.text }}
        </li>
      </transition-group>
    </div>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
import gsap from 'gsap'
export default {
  setup() {
    const beforeEnter = (el) => {
      el.style.opacity = 0;
      el.style.transform ='translateY(100px)';
    }
    const enter = (el,done) => {
      gsap.to(el,{
        y:0,
        opacity : 1,
        duration:0.8,
        onComplete:done,
        delay:el.dataset.index * 0.2
      })
    }
    const icons = ref([
      { name: "alternate_email", text: "by email" },
      { name: "local_phone", text: "by phone" },
      { name: "local_post_office", text: "by post" },
      { name: "local_fire_department", text: "by smoke signal" },
    ]);

    return { icons ,enter ,beforeEnter };
  },
};
</script>

<style>
</style>