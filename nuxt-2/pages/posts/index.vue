<template>
  <div class="posts-page">
    <PostList :posts="loadedPosts"/>
  </div>
</template>

<script>
import PostList from "@/components/Posts/PostList";
export default {
  components: {
    PostList
  },
  fetch(context) {
    if(context.store.state.loadedPosts.length > 0){
      return null;
    }
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve({
          loadedPosts: [
            {
              id: "1",
              title: "First Post",
              previewText: "This is our first  post!",
              thumbnail:
                "https://static.techspot.com/images2/news/bigimage/2018/07/2018-07-10-image-35.jpg"
            },
            {
              id: "2",
              title: "Second Post",
              previewText: "This is our first  post!",
              thumbnail:
                "https://static.techspot.com/images2/news/bigimage/2018/07/2018-07-10-image-35.jpg"
            },
            {
              id: "3",
              title: "Third Post",
              previewText: "This is our first  post!",
              thumbnail:
                "https://static.techspot.com/images2/news/bigimage/2018/07/2018-07-10-image-35.jpg"
            }
          ]
        });
      }, 500);
    })
      .then(data => {
        context.store.commit("setPosts", data.loadedPosts);
      })
      .catch(e => {
        context.error(new Error());
      });
  },
  computed :{
    loadedPosts(){
      return this.$store.getters.loadedPosts;
    }
  },
  created() {
    this.$store.dispatch("setPosts", this.loadedPosts);
  }
};
</script>

<style scoped>
.posts-page {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
