<template>
  <div class="home">
    <h1>Details</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="post">
      <h3>{{ post.title }}</h3>
      <p class="pre">{{ post.body }}</p>
    </div>
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import getPost from "../composables/GetPost";

export default {
  props: ["id"],
  setup(props) {
    const { post, error, load } = getPost(props.id);

    load();

    return { post, error };
  },
};
</script>

<style>
.post {
  max-width: 1200px;
  margin: 0 auto;
}

.post p {
  color: #444;
  line-height: 1.5em;
  margin-top: 40px;
}

.pre {
  white-space: pre-wrap;
}
</style>
