<template>
  <main>
    <section v-if="post">
      <nav class="mb-8" aria-label="go back">
        <router-back class="block" />
      </nav>

      <article>
<!--         <img
          v-if="post.cover"
          class="cover-image"
          :src="post.cover"
        > -->
        <h6 class="inline py-1 px-2 mr-1 bg-gray text-white text-sm font-medium rounded-sm">{{ post.category }}</h6>
        <h1 class="">{{ post.title }}</h1>
        <p class="mt-1 mb-8 text-primary-600 dark:text-primary-400">{{ post.description }}</p>
        <nuxt-content :document="post" />
        <!-- <div v-if="post.gallery" class="nuxt-content">
          <img
            v-for="image in post.gallery"
            class="image"
            :key="image.id"
            :src="image"
          >
        </div> -->
      </article>
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let post;
    try {
      post = await $content("projects", params.project).fetch();
    } catch (e) {
      error({ message: "Project not found" });
    }
    return { post };
  },
}
</script>

<style>
/* purgecss ignore */
.video-container {
  position: relative;
  padding-bottom: 56.25%; /*16:9*/
  padding-top: 30px; 
  height: 0; 
  overflow: hidden;
  margin: 2rem 0px;
  position: sticky;
  top: 65px;
}
/* purgecss ignore */
.video-container iframe,
.video-container object,
.video-container embed {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>