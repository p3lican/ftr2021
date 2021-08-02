<template>
  <main>
    <section class="self-center flex flex-1 flex-col md:flex-row items-center justify-center max-w-screen-xl">
      <img src="../assets/img/alejandro-de-los-rios.JPG" class="w-full max-w-xs ">
      <div class="sm:p-5">
      <h1 class="title text-center mt-5">From The River Films | Alejandro de los Rios</h1>
      <h2 class="text-center dark:text-white">Just your typical Nicaraguan-born, half-Cuban, half-Venezuelan filmmaker based in New Orleans.</h2>
    </div>
    </section>


    <div class="flex flex-col md:flex-row items-center justify-center">
    <section class="flex-1 max-w-screen-lg mt-5 md:mt-0">
      <h3 class="subtitle text-center inline py-1 px-2 mr-1 text-white text-sm font-medium rounded-sm">My Past Clients Include</h3>
      <div class="self-center flex flex-wrap items-center justify-center mt-3 bg-gradient-to-t from-black to-transparent">
      <picture class="h-20 block max-w-xs w-1/3 sm:w-1/4 md:w-1/6 lg:w-1/6 p-1" v-for="client in theClients">
      <img :src="require(`~/assets`+client.logo)" :alt="client.title" :title="client.title" class="w-full h-full object-contain">
      </picture>
      </div>
    </section>
    <section class="flex-1 max-w-screen-lg mt-5 md:mt-0">
      <h3 class="subtitle text-center inline py-1 px-2 mr-1 text-white text-sm font-medium rounded-sm">Awards & Laurels</h3>
      <div class="self-center flex flex-wrap items-center justify-center mt-3">
      <picture class="h-20 block max-w-xs w-1/2 p-1" v-for="award in theAwards">
      <img :src="require(`~/assets`+award.logo)" :alt="award.title" :title="award.title" class="w-full h-full object-contain">
      </picture>
      </div>
    </section>
    </div>
    <!-- <section class="mt-8">
      <h3 class="text-primary-600 dark:text-primary-400 max-w-5xl mx-auto">Latest blog post</h3>
      <posts post-type="blog" :amount="1" />
    </section> -->
  </main>
</template>

<script>
export default {
  mounted() {
    console.log(this.$route.params.slug)
  },

  async asyncData({ $content, route }){ 
    const theClients = await $content("client").sortBy('createdAt').fetch();
    const theAwards = await $content("award").sortBy('createdAt').fetch();

    return {
      theClients,
      theAwards
    };
  },

}
</script>
