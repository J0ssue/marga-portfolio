<template>
  <div class="bg-black text-white lausanne relative" id="layout-default">
    <nav class="navigation w-full z-10 flex base-font-size px-8 py-6">
      <div class="">
        <p class="nav-text-shadow" to="#" v-text="nav.brand" />
      </div>
      <div class="flex-1 pl-8"></div>
    </nav>
    <p class="home__hero-text hero-text">
      Graphic designer from Lisbon,<br />
      recently graduated from London<br />
      College of Communication with<br />
      an MA in
      <a
        class="apoc-revelations-italic italic-text-shadow hand-cursor"
        href="http://magmd.uk/"
        target="_blank"
      >
        Graphic Media Design<br />
      </a>
      Continuously researching on<br />
      editorial strategies, navigation<br />
      and
      <button
        @click="openCreativityDocument"
        class="apoc-revelations-italic italic-text-shadow focus:outline-none hand-cursor"
      >
        creativity</button
      >, working in identity,<br />
      editorial and digital design.,
    </p>
    <nuxt />
    <footer class="flex px-8 pb-8">
      <div>
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
          <button class="focus:outline-none" @click="toggleMenu">
            Projects
          </button>
        </div>
        <a class="block gray-text" :href="`mailto:${myEmail}`" target="_blank">
          E-mail for comissions or collaborations
        </a>
      </div>
      <div class="separator flex-1"></div>
      <div>
        <div class="flex justify-end">
          <button class="focus:outline-none" @click="scrollToTop">
            <img src="/images/icons/arrow-up.png" alt="arrow up" />
          </button>
        </div>
        <div class="gray-text">
          &copy; Margarida Morais
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import menu from '~/helpers/dropdown'
export default {
  data() {
    return {
      isMenuOpen: false,
      menu,
      myEmail: 'example@example.com',
      nav: {
        brand: 'Margarida Morais',
        contact: 'Contact for commissions or collaborations'
      },
      footer: {
        email: 'Contact for project enquiries. CV available on request'
      }
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
    },
    openCreativityDocument() {
      window.open('/pdfs/No_Singular_Narrative.pdf', '_blank')
    },
    scrollToTop() {
      window.scroll({
        top: 0,
        left: 0,
        behavior: 'smooth'
      })
    }
  }
}
</script>

<style lang="scss" scope>
.main-menu {
  color: #828282;
  left: 0;
  bottom: 10px;
  opacity: 0;
  pointer-events: none;
}
</style>
