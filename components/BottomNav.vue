<template>
  <div class="px-10 flex justify-between items-end w-full text-white">
    <!-- col -->
    <div class="flex-1">
      <div class="relative">
        <ul
          class="main-menu absolute"
          :class="{
            'fade-down': !isMenuOpen,
            'fade-up': isMenuOpen
          }"
        >
          <li v-for="(link, i) in menu" :key="i">
            <nuxt-link
              class="hover:text-white focus:outline-none"
              to=""
              @click.native="navigateTo(link.tag)"
              v-text="link.name"
            />
          </li>
        </ul>
        <button class="focus:outline-none" @click="toggleMenu">Projects</button>
      </div>
    </div>
    <!-- col -->
    <div class="flex-1 text-center">
      <div>
        <p class="nav-gray-link">contact@morais-margarida.com</p>
        <button>Contact</button>
      </div>
    </div>
    <!-- col -->
    <div class="flex-1 text-right">
      <div>
        <a
          class="block gav-gray-link"
          href="https://shop.magculture.com/products/a-line-which-forms-a-volume-3?_pos=1&_sid=1d27693fe&_ss=r"
          target="_blank"
        >
          MagCulture<br />
          Libros Mutantes
        </a>
        <button>Features</button>
      </div>
    </div>
  </div>
</template>

<script>
import menu from '~/helpers/dropdown'
export default {
  data() {
    return {
      isMenuOpen: false,
      menu
    }
  },
  methods: {
    navigateTo(link) {
      let element = document.querySelector('#' + link)
      element.scrollIntoView({
        block: 'start',
        behavior: 'smooth'
      })
      this.toggleMenu()
    },
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen
    }
  }
}
</script>

<style lang="scss" scoped>
.nav-gray-link {
  color: #828282;
}
.main-menu {
  color: #828282;
  left: 0;
  bottom: 10px;
  opacity: 0;
  pointer-events: none;
}
</style>
