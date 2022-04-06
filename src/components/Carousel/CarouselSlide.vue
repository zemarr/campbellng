<template>
    <div class="carousel-slide w-screen min-h-screen">
        <transition name="fade">
            <slot></slot>
        </transition>
    </div>
</template>

<script>
    export default {
        name: 'CarouselSlide'
    }
</script>
<style scoped>
    .fade-enter-active, .fade-leave-active {
        transition: opacity 3s ease-in-out;
    }
    .fade-enter-from, .fade-leave-to {
        opacity: 0;
    }
    .fade-enter-to, .fade-leave-active {
        opacity: 1;
    }
</style>
