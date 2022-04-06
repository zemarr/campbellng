<template>
  <div class="w-full relative flex items-center overflow-hidden">
    <div class="left">
      <Carousel v-slot="{ currentSlide }">
        <CarouselSlide v-for="(slide, index) in carouselSlides" :key="index">
          <div v-show="currentSlide === index + 1" class="info absolute max-h-full h-screen w-full top-0 left-0">
            <img :src="require(`./assets/${slide}.jpg`)" alt="" class="w-full h-full object-cover">
          </div>
        </CarouselSlide>
      </Carousel>
    </div>
    <div class="right slow-transition w-full sm:w-[35%] md:w-[30%] lg:w-[20%] h-screen py-8 px-5 absolute top-0 right-0 z-[1000]">
      <!-- Hamburger -->
      <!-- <button @click="menuOpen = !menuOpen" class="absolute top-[60px] -left-[50px] py-2 px-4 rounded-l-full" :class="menuOpen ? 'bg-transparent' : 'bg-black'">
        <span v-show="!menuOpen">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-7 w-7 text-white" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM9 15a1 1 0 011-1h6a1 1 0 110 2h-6a1 1 0 01-1-1z" clip-rule="evenodd" />
          </svg>
        </span>
        <span v-show="menuOpen">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-7 w-7 text-white" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd" />
          </svg>
        </span>
      </button> -->
      <NavbarComponent></NavbarComponent>
    </div>
    <!-- toggle menu class -->
     <!-- :class="[windowWidth < 1024 ? '-right-[200px]' : 'right-0', menuOpen ? 'right-0' : '-right-[200px]']" -->
    
    <router-view></router-view>
  </div>
</template>

<script>
import NavbarComponent from '@/components/Navbar/NavbarComponent.vue'
import Carousel from '@/components/Carousel/CarouselWrap.vue'
import CarouselSlide from '@/components/Carousel/CarouselSlide.vue'
import { onMounted, onUnmounted, ref } from 'vue'

export default {
  name: 'App',
  components: {
    NavbarComponent,
    Carousel,
    CarouselSlide
  },
  setup () {
    let windowWidth = ref(window.innerWidth)
    let menuOpen = ref(false)
    
    const carouselSlides = [
      "Backg-1",
      "Backg-2",
      "Backg-3",
      "Backg-4",
      "Backg-5",
      "Backg-6"
    ]

    const onWidthChange =  () => {
      windowWidth.value = window.innerWidth
    }

    onMounted(() => {
      window.addEventListener('resize', onWidthChange)
    })
    onUnmounted(() => {
      window.removeEventListener('resize', onWidthChange)
    })

    return {
      carouselSlides,
      windowWidth,
      menuOpen
    }
  }
}
</script>

<style>
</style>
