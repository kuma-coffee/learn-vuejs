<template>
  <div class="home">
    <h1>Home</h1>
    <!-- <PostList v-if="showPosts" :posts="posts" />
    <button @click="showPosts = !showPosts">toggle posts</button>
    <button @click="posts.pop()">delete a post</button> -->
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="posts" />
    </div>
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import PostList from "../components/PostList.vue";
import getPosts from "../composables/GetPosts";

export default {
  name: "HomeView",
  components: { PostList },
  setup() {
    // const showPosts = ref(true);

    const { posts, error, load } = getPosts();

    load();

    return { posts, error };
  },
};
</script>
