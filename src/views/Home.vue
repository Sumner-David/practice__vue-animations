<template>
  <div class="home">
    <Toast v-if="showToast" />
    <Todos @badValue="triggerToast" />

    <button @click="showP = !showP">
      Toggle
    </button>

    <transition name="fade">
      <div v-if="showP">
        Hello, Ninjas
      </div>
    </transition>
  </div>
</template>

<script>
import { ref } from 'vue'
import Toast from '../components/Toast'
import Todos from '../components/Todos'

export default {
  components: { Toast, Todos },
  setup() {
    const showToast = ref(false)

    const triggerToast = () => {
      showToast.value = true;
      setTimeout(() => showToast.value = false, 3000)
    }

    const showP = ref(false)

    return { showToast, triggerToast, showP }
  }
}
</script>

<style>
  .fade-enter-from {
    opacity: 0
  }
  .fade-enter-to {
  }
  .fade-enter-active {
    transition: all 0.5s linear
  }

  .fade-leave-from {
  }
  .fade-leave-to {
    opacity:0
  }

  .fade-leave-active {
    transition: all 0.5s ease
  }

</style>