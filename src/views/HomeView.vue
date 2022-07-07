<template>
  <div class="container">
    <h1 class="text-center">Home Page</h1>
    <transition name="fade">
      <toast v-if="showToast" />
    </transition>
    <todos @badValue="triggerToast" />
  </div>
</template>

<script>
import todos from "../components/todosView.vue";
import toast from "../components/toastView.vue";
import { ref } from "@vue/reactivity";
export default {
  components: { todos, toast },
  setup() {
    const showToast = ref(false);
    const triggerToast = () => {
      showToast.value = true;
      setTimeout(() => (showToast.value = false), 3000);
    };
    return {
      showToast,
      triggerToast,
    };
  },
};
</script>
<style scoped>
/*.fade-enter-from {
  opacity: 0;
  transform: translateY(-60px);
}
.fade-enter-to {
  opacity: 1;
  transform: translateY(0);
}*/
.fade-enter-active{
  animation: wobble 0.5s ease;
}
.fade-leave-active {
  transition: all 1s ease;
}
.fade-leave-from {
  opacity: 1;
  transform: translateY(0);
}
.fade-leave-to {
  opacity: 0;
  transform: translateY(-60px);
}
/*.fade-leave-active {transition: all 2s ease;}*/
@keyframes wobble {
  0% {transform: translateY(-60px);}
  50% {transform: translateY(0);}
  60% {transform: translateX(8px);}
  70% {transform: translateX(-8px);}
  80% {transform: translateX(4px);}
  90% {transform: translateX(-4px);}
  100% {transform: translateX(0);}
}
</style>
