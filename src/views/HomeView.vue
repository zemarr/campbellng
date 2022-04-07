<template>
  <div class="home absolute top-0 left-0 w-full mx-[40px] mr-0 py-[40px]" :class="[windowWidth < 1024 ? 'max-w-full' : 'max-w-[78%]']">
    <!-- <h1 class="text-[32px] text-white">HOME PAGE</h1> -->
  </div>
</template>

<script>
import { onMounted, onUnmounted, ref } from 'vue'

export default {
  name: 'HomeView',
  components: {},
  setup () {
    const windowWidth = ref(window.innerWidth)
    const onWidthChange = () => {
      windowWidth.value = window.innerWidth
    }

    onMounted(() => {
      window.addEventListener('resize', onWidthChange)
    })
    onUnmounted(() => {
      window.removeEventListener('resize', onWidthChange)
    })

    return {
      windowWidth
    }
  }
}
</script>
