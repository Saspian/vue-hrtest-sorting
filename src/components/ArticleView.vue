<template>
  <div class="article-row">
    <h3 class="article-header">{{ article.title}}</h3>
    <div class="data">
      <h3>{{ article.upvotes }}</h3>
      <h3>{{ article.date }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "ArticleView",
  props: {
    article: Object
  }
};
</script>
<style scoped>
.article-row {
  display: flex;
  justify-content: space-between;
  align-content: center;
}
.article-header {
  width: 700px;
}
.data {
  width: 200px;
  display: flex;
  justify-content: space-between;
  padding: 0px 40px;
}
</style>