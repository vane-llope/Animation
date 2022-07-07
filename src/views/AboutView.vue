<template>
  <div class="container mt-3">
    <div class="text-center">
      <transition @before-enter="beforeEnter" @enter="enter" appear>
        <h1 v-if="showTitile">ABOUT</h1>
      </transition>
      <div class="container">
        <transition @before-enter="leftEnterB" @enter="leftEnterE" appear>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima hic
          consectetur optio, reiciendis, blanditiis labore culpa, enim incidunt
          quisquam suscipit quasi. Eos tenetur vel nisi magnam officia!
          Repudiandae vero assumenda distinctio alias ut quidem minima nam,
          porro autem in impedit natus possimus dignissimos incidunt quae fugiat
          dolorum facere, modi
        </p>
         </transition>
          <transition @before-enter="rightEnterB" @enter="leftEnterE" appear>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima hic
          consectetur optio, reiciendis, blanditiis labore culpa, enim incidunt
          quisquam suscipit quasi. Eos tenetur vel nisi magnam officia!
          Repudiandae vero assumenda distinctio alias ut quidem minima nam,
          porro autem in impedit natus possimus dignissimos incidunt quae fugiat
          dolorum facere, modi
        </p>
          </transition>
         <transition @before-enter="leftEnterB" @enter="leftEnterE" appear>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima hic
          consectetur optio, reiciendis, blanditiis labore culpa, enim incidunt
          quisquam suscipit quasi. Eos tenetur vel nisi magnam officia!
          Repudiandae vero assumenda distinctio alias ut quidem minima nam,
          porro autem in impedit natus possimus dignissimos incidunt quae fugiat
          dolorum facere, modi
        </p>
         </transition>
      </div>
    </div>
  </div>
</template>
<script>
import gsap from "gsap";
import { ref } from "@vue/reactivity";
export default {
  setup() {
    const leftEnterB = (el) => {
       el.style.transform = "translateX(-60px)";
       el.style.opacity = 0;
    }
    const leftEnterE  = (el ,done) => {
      gsap.to(el,{
        x:0,
        opacity:1,
        duration:1,
        onComplete :done
      })
    }
    const rightEnterB = (el) => {
       el.style.transform = "translateX(60px)";
       el.style.opacity = 0;
    }
    const showTitile = ref(true);
    const beforeEnter = (el) => {
      el.style.transform = "translateY(-60px)";
      el.style.opacity = 0;
    };
    const enter = (el, done) => {
      gsap.to(el, {
        y: 0,
        opacity: 1,
        duration: 1,
        ease: "bounce.out",
        onComplete: done,
      });
    };
    /* const afterEnter = (el) => {
    el.style.color = 'gray'
      setTimeout(() => (showTitile.value = false)), 2000;

    };
 
    const beforeleave = () => {};
    const leave = () => {};
    const afterleave = () => {};*/
    return {
      beforeEnter,
      enter,
      showTitile,
      leftEnterB,
      leftEnterE,
      rightEnterB,
    };
  },
};
</script>


<style>
/*.
.fade-leave-to {
  opacity: 0;
}
fade-enter-to , .fade-leave-from{opacity: 1; transform: translate(0);}
.fade-enter-active,
.fade-leave-active {
  transition: all 2s ease;
}*/
</style>
