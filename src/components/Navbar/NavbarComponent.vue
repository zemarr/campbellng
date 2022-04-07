<template>
    <nav class="nav">
      <div class="relative flex flex-col items-center">
        <div class="logo w-[95px] h-[80px] cursor-pointer z-40" @click="toggleNav()">
          <img src="../../assets/logo.png" alt="" class="w-full h-full">
        </div>
        <span class="nav-line block h-[2px] bg-white my-2" :class="[isNavActive ? 'w-full' : 'w-0']"></span>
        <div class="nav-wrap w-full overflow-hidden min-h-max absolute left-0 z-30" :class="[isNavActive ? 'top-[100px] opacity-[1] z-40 delayed' : 'top-0 opacity-0 z-30 delayed']">
          <div class="nav-items  fast-transition relative grid grid-cols-2 flex-nowrap w-[200%] overflow-hidden">
            <ul class="w-[100%] text-center text-white overflow-hidden relative">
              <li class="w-full cursor-pointer" @click="viewHistory">HISTORY</li>
              <li class="w-full cursor-pointer" @click="viewPeople">PEOPLE</li>
              <li class="w-full cursor-pointer" @click="viewProjects">PROJECTS</li>
              <li class="w-full cursor-pointer" @click="viewContact">CONTACT</li>
            </ul>
            <ul v-show="toHistory" class="history slide-screen relative flex flex-col justify-center items-center text-white w-[100%]">
              <li class="mx-auto font-medium text-[16px] mb-4">HISTORY</li>
              <li class="mx-auto text-[15px]">Ọmọ Ọwá</li>
              <li class="mx-auto text-[15px]">Ọmọ ẹkùn</li>
              <button @click="goBack" class="block my-4">
                <svg class="text-white" width="12" height="15" viewBox="0 0 11 18" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
                  <path d="M9.84853 2.84853C10.3172 2.3799 10.3172 1.6201 9.84853 1.15147C9.3799 0.682843 8.6201 0.682843 8.15147 1.15147L9.84853 2.84853ZM2 9L1.15147 8.15147C0.682843 8.6201 0.682843 9.3799 1.15147 9.84853L2 9ZM8.15147 16.8485C8.6201 17.3172 9.3799 17.3172 9.84853 16.8485C10.3172 16.3799 10.3172 15.6201 9.84853 15.1515L8.15147 16.8485ZM8.15147 1.15147L1.15147 8.15147L2.84853 9.84853L9.84853 2.84853L8.15147 1.15147ZM1.15147 9.84853L8.15147 16.8485L9.84853 15.1515L2.84853 8.15147L1.15147 9.84853Z" fill="currentColor"/>
                </svg>
              </button>
            </ul>
            <ul v-show="toPeople" class="people slide-screen relative flex flex-col justify-center items-center text-white w-[100%]">
              <li class="mx-auto font-medium text-[16px] mb-4">PEOPLE</li>
              <li class="mx-auto text-[15px]">
                <a href="http://toni.campbell.ng">Oluwatoni</a>
              </li>
              <li class="mx-auto text-[15px]">Oluwatona</li>
              <!-- <li class="mx-auto text-[15px]">Alolade</li>
              <li class="mx-auto text-[15px]">Oluwateni</li> -->
              <button @click="goBack" class="block my-4">
                <svg class="text-white" width="12" height="15" viewBox="0 0 11 18" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
                  <path d="M9.84853 2.84853C10.3172 2.3799 10.3172 1.6201 9.84853 1.15147C9.3799 0.682843 8.6201 0.682843 8.15147 1.15147L9.84853 2.84853ZM2 9L1.15147 8.15147C0.682843 8.6201 0.682843 9.3799 1.15147 9.84853L2 9ZM8.15147 16.8485C8.6201 17.3172 9.3799 17.3172 9.84853 16.8485C10.3172 16.3799 10.3172 15.6201 9.84853 15.1515L8.15147 16.8485ZM8.15147 1.15147L1.15147 8.15147L2.84853 9.84853L9.84853 2.84853L8.15147 1.15147ZM1.15147 9.84853L8.15147 16.8485L9.84853 15.1515L2.84853 8.15147L1.15147 9.84853Z" fill="currentColor"/>
                </svg>
              </button>
            </ul>
            <ul v-show="toProjects" class="projects slide-screen relative flex flex-col justify-center items-center text-white w-[100%]">
              <li class="mx-auto font-medium text-[16px] mb-4">PROJECTS</li>
              <li class="mx-auto text-[15px]">Art</li>
              <li class="mx-auto text-[15px]">Writing</li>
              <li class="mx-auto text-[15px]">Philantrophy</li>
              <li class="mx-auto text-[15px]">Corporate</li>
              <button @click="goBack" class="block my-4">
                <svg class="text-white" width="12" height="15" viewBox="0 0 11 18" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
                  <path d="M9.84853 2.84853C10.3172 2.3799 10.3172 1.6201 9.84853 1.15147C9.3799 0.682843 8.6201 0.682843 8.15147 1.15147L9.84853 2.84853ZM2 9L1.15147 8.15147C0.682843 8.6201 0.682843 9.3799 1.15147 9.84853L2 9ZM8.15147 16.8485C8.6201 17.3172 9.3799 17.3172 9.84853 16.8485C10.3172 16.3799 10.3172 15.6201 9.84853 15.1515L8.15147 16.8485ZM8.15147 1.15147L1.15147 8.15147L2.84853 9.84853L9.84853 2.84853L8.15147 1.15147ZM1.15147 9.84853L8.15147 16.8485L9.84853 15.1515L2.84853 8.15147L1.15147 9.84853Z" fill="currentColor"/>
                </svg>
              </button>
            </ul>
            <ul v-show="toContact" class="history slide-screen relative flex flex-col justify-center items-center text-white w-[100%]">
              <li class="mx-auto font-medium text-[16px] mb-4">CONTACTS</li>
              <li class="mx-auto text-[15px]">
                <a href="mailto:info@campbell.ng" class="mail-icon">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                </svg>
                </a>
              </li>
              <button @click="goBack" class="block my-4">
                <svg class="text-white" width="12" height="15" viewBox="0 0 11 18" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
                  <path d="M9.84853 2.84853C10.3172 2.3799 10.3172 1.6201 9.84853 1.15147C9.3799 0.682843 8.6201 0.682843 8.15147 1.15147L9.84853 2.84853ZM2 9L1.15147 8.15147C0.682843 8.6201 0.682843 9.3799 1.15147 9.84853L2 9ZM8.15147 16.8485C8.6201 17.3172 9.3799 17.3172 9.84853 16.8485C10.3172 16.3799 10.3172 15.6201 9.84853 15.1515L8.15147 16.8485ZM8.15147 1.15147L1.15147 8.15147L2.84853 9.84853L9.84853 2.84853L8.15147 1.15147ZM1.15147 9.84853L8.15147 16.8485L9.84853 15.1515L2.84853 8.15147L1.15147 9.84853Z" fill="currentColor"/>
                </svg>
              </button>
            </ul>
          </div>
        </div>
      </div>
    </nav>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'NavbarComponent',
  components: {
  },
  setup () {
    const isNavActive = ref(false)
    const toHistory = ref(false)
    const toPeople = ref(false)
    const toProjects = ref(false)
    const toContact = ref(false)

    const toggleNav = async () => {
      isNavActive.value = !isNavActive.value
      if (isNavActive.value === false) {
        goBack()
      }
    }

    const goBack = async () => {
      const navItems = document.querySelector('.nav-items')
      navItems.style.transform = 'translateX(0)'
      toHistory.value = false
      toPeople.value = false
      toProjects.value = false
      toContact.value = false
    }

    const viewHistory = async () => {
      const navItems = document.querySelector('.nav-items')
      toHistory.value = true
      navItems.style.transform = 'translateX(-50%)'
    }
    const viewPeople = async () => {
      const navItems = document.querySelector('.nav-items')
      toPeople.value = true
      navItems.style.transform = 'translateX(-50%)'
    }
    const viewProjects = async () => {
      const navItems = document.querySelector('.nav-items')
      toProjects.value = true
      navItems.style.transform = 'translateX(-50%)'
    }
    const viewContact = async () => {
      const navItems = document.querySelector('.nav-items')
      toContact.value = true
      navItems.style.transform = 'translateX(-50%)'
    }

    return {
      isNavActive,
      toggleNav,
      goBack,
      toHistory,
      toPeople,
      toProjects,
      toContact,
      viewHistory,
      viewPeople,
      viewProjects,
      viewContact
    }
  }
}
</script>

<style scoped>

  .nav-wrap, .nav-line {
    transition: .8s ease-in-out;
  }

  .delayed {
    transition-delay: 1s;
  }
  .no-delay {
    transition-delay: 0s;
  }
</style>
