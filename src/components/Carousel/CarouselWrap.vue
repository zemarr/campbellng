<template>
    <div class="carousel-wrap relative w-screen h-screen overflow-hidden">
        <slot :currentSlide="currentSlide"></slot>
    </div>
</template>

<script>
import { ref, onMounted } from 'vue'

export default {
  name: 'CarouselWrap',
  setup () {
    const currentSlide = ref(1)
    const getSlideCount = ref(null)
    const changeSlide = () => {
      if (currentSlide.value === getSlideCount.value) {
        currentSlide.value = 1
        return
      }
      currentSlide.value += 1
    }
    const autoPlay = () => {
      setInterval(() => {
        changeSlide()
      }, 20000)
    }

    onMounted(() => {
      getSlideCount.value = document.querySelectorAll('.carousel-slide').length
      autoPlay()
    })

    return {
      currentSlide,
      getSlideCount
    }
  }
}
</script>
<style>
</style>
