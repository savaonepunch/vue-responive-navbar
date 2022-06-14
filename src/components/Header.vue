<template>
  <div class="headerDesktop">
    <div class="logo">
      <a v-if="!darkMode" href="#"><img src="../assets/images/LogoDark.png" alt="Logo" /></a>
      <a v-else href="#"><img src="../assets/images/Logo.png" alt="Logo" /></a>
    </div>
    <div class="navList">
      <div class="navItem"><a href="#">Home</a></div>
      <div class="navItem"><a href="#">Docs</a></div>
      <div class="navItem"><a href="#">API</a></div>
      <div class="navItem"><a href="#">Examples</a></div>
      <div class="navItem"><a href="#">Community</a></div>
      <div @click="switchTheme" class="navItem">
        <i v-if="!darkMode" class="fa-solid fa-sun fa-xl"></i>
        <i v-else class="fa-solid fa-moon fa-xl"></i>
      </div>
    </div>
  </div>
  <Transition>
    <div v-if="!menuOpen" class="headerMobile">
      <div @click="openMenu" class="menuBtn">
        <img v-if="!darkMode" src="../assets/images/menubtndark.png" alt="" />
        <img v-else src="../assets/images/menubtn.png" alt="" />
      </div>
      <div class="logo">
        <a v-if="!darkMode" href="#"><img src="../assets/images/LogoDark.png" alt="Logo" /></a>
        <a v-else href="#"><img src="../assets/images/Logo.png" alt="Logo" /></a>
      </div>
    </div>
    <div v-else class="headerMobileOpen">
      <div @click="closeMenu" class="menuBtn">
        <img v-if="!darkMode" src="../assets/images/closebtndark.png" alt="" />
        <img v-else src="../assets/images/closebtn.png" alt="" />
      </div>
      <div class="logo">
        <a v-if="!darkMode" href="#"><img src="../assets/images/LogoDark.png" alt="Logo" /></a>
        <a v-else href="#"><img src="../assets/images/Logo.png" alt="Logo" /></a>
      </div>
      <div @click="switchTheme" class="themeBtn">
        <i v-if="!darkMode" class="fa-solid fa-sun fa-2xl"></i>
        <i v-else class="fa-solid fa-moon fa-2xl"></i>
      </div>

      <div class="navList">
        <div class="navItem"><a href="#">Home</a></div>
        <div class="navItem"><a href="#">Docs</a></div>
        <div class="navItem"><a href="#">API</a></div>
        <div class="navItem"><a href="#">Examples</a></div>
        <div class="navItem"><a href="#">Community</a></div>
      </div>
    </div>
  </Transition>
</template>

<script setup>
import { ref, watch, onMounted } from "vue";

const menuOpen = ref(false);
const darkMode = ref(true);

const openMenu = () => {
  menuOpen.value = true;
};

const closeMenu = () => {
  menuOpen.value = false;
};

const switchTheme = () => {
  darkMode.value = !darkMode.value;
};

watch(menuOpen, () => {
  if (menuOpen.value) {
    console.log("menu is open");
  }
});

watch(darkMode, () => {
  if (darkMode.value) {
    document.body.classList.remove('light-mode')
    document.body.classList.add('dark-mode')
  }
  else {
    document.body.classList.remove('dark-mode')
    document.body.classList.add('light-mode')
  }
});

onMounted(() => {
  document.body.classList.add('dark-mode')
})

</script>
