<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="title">Voorbeelden</h1>
      <posts post-type="projects" :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts;
    try {
      posts = await $content("voorbeelden").fetch();
    } catch (e) {
      error({ message: "Er zijn geen voorbeelden gevonden" });
    }
    return { posts };
  },
}
</script>
