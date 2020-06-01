<template>
  <div class="home w-full">
    <header class="mb-32">
      <div class="home__hero py-40"></div>
      <BottomNav />
    </header>
    <main>
      <SectionBase
        :settings="{
          slug: project.slug,
          title: project.title,
          subtitle: project.subtitle,
          description: project.description,
          images: project.images
        }"
        v-for="(project, i) in projects.projects"
        :key="i"
      />
    </main>
  </div>
</template>

<script>
import projects from '~/helpers/projects'
import SectionBase from '~/components/SectionBase'
import BottomNav from '~/components/BottomNav'
export default {
  components: {
    SectionBase,
    BottomNav
  },
  data() {
    return {
      title: 'Margarida Morais',
      projects
    }
  },

  head() {
    return {
      title: this.title,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: 'description',
          name: 'description',
          content: 'My custom description'
        }
      ]
    }
  }
}
</script>
