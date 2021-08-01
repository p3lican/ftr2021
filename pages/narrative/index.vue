<template>
  <main>
    <section v-if="theProjects" class="w-full max-w-5xl mx-auto">
      <h1 class="title">Narrative</h1>
      <div class="flex flex-col flex-wrap sm:flex-row">
      <nuxt-link  class=" mt-5 text-center p-2 sm:w-1/2 md:w-1/3" v-for="(project, index) in theProjects" :key="project.index" :to="project.path">
        <article>
          <img :src="project.cover">
          <h2 class="my-5">{{project.title}}</h2>
        </article>
      </nuxt-link>
  </div>


    </section>
  </main>
</template>

<script>
export default {
  mounted() {
    console.log(this.$route.params.slug)
  },

  async asyncData({ $content, route }){ 
    const theProjects = await $content("projects").sortBy('createdAt').where({
      category: { $eq:  route.name }
    }).fetch();

    return {
      theProjects,
    };
  },

}
</script>
