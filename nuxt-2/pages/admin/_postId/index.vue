<template>
  <div class="admin-post-page">
    <section class="update-form">
      <AdminPostForm :post="loadedPost" @submit="onSubmitted"/>
    </section>
  </div>
</template>

<script>
import axios from "axios";
import AdminPostForm from "@/components/Admin/AdminPostForm";
export default {
  layout: "admin",
  components: {
    AdminPostForm
  },
  async asyncData(context) {
    return axios
      .get(
        "https://nuxt-blog-b6948.firebaseio.com/posts/" +
          context.route.params.postId +
          ".json"
      )
      .then(res => {
        console.log(res)
        return {
          loadedPost: res.data
        };
      })
      .catch(e => context.error(e));
  },
  methods: {
    onSubmitted(editedPost) {
      axios
        .put(
          "https://nuxt-blog-b6948.firebaseio.com/posts/" +
            this.$route.params.postId +
            ".json",
          editedPost
        )
        .then(res => console.log(res))
        .catch(e => console.error(e));
    }
  }
};
</script>

<style scoped>
.update-form {
  width: 90%;
  margin: 20px auto;
}
@media (min-width: 768px) {
  .update-form {
    width: 500px;
  }
}
</style>
