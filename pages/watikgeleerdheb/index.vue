<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="title">Wat ik geleerd heb</h1>
      <posts post-type="blog" :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts;
    try {
      posts = await $content("hebikzogeleerd").fetch();
    } catch (e) {
      error({ message: "Er is niets noppes nada gevonden" });
    }
    return { posts };
  },
}
</script>
