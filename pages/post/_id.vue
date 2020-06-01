<template>
  <article class="post">
    <header class="post-header">
      <div class="post-title">
        <h1>Post title</h1>
        <nuxt-link to="/">
          <i class="el-icon-back"></i>
        </nuxt-link>
      </div>
      <div class="post-info">
        <small>
          <i class="el-icon-time"></i>
          {{new Date().toLocaleString() }}
        </small>
        <small>
          <i class="el-icon-view"></i>
          42
        </small>
      </div>
      <div class="post-image">
        <img
          src="https://avatars.mds.yandex.net/get-pdb/2038916/11d0def9-6704-4a27-ba3f-3f09ef75b02d/s1200"
          alt="post-img"
        />
      </div>
    </header>
    <main class="post-content">
      <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Dolores at asperiores quisquam enim? Incidunt doloribus in reiciendis, nam enim velit iusto rem maiores similique possimus accusantium, ea delectus cupiditate ab.</p>
    </main>
    <footer>
      <form action></form>
      <AppCommentForm v-if="canAddComment" @created="createCommentHandler" />
      <div class="comments" v-if="true">
        <app-comment v-for="comment in 4" :key="comment" :comment="comment"></app-comment>
      </div>
      <div class="text-center" v-else>Комментариев нет</div>
    </footer>
  </article>
</template>

<script>
import AppComment from "@/components/Main/Comment";
import AppCommentForm from "@/components/Main/CommentForm";
export default {
  validate({ params }) {
    return Boolean(params.id);
  },
  data() {
    return {
      canAddComment: true
    };
  },
  components: { AppComment, AppCommentForm },
  methods: {
    createCommentHandler() {
      this.canAddComment = false;
    }
  }
};
</script>


<style lang="scss" scoped>
.post {
  max-width: 600px;
  margin: 0 auto;
}

.post-title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.post-info {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.5rem;
}

.post-image img {
  width: 100%;
  height: auto;
}
.post-header {
  margin-bottom: 0.5rem;
}

.post-content {
  margin-bottom: 2rem;
}
</style>
