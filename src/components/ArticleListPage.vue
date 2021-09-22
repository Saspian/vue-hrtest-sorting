<template>
  Sort by
  <select
    class="btn"
    v-model="voteOrder"
    name="voteOrder"
    @click="$emit('sort-by-votes', voteOrder)"
  >
    <option value="-1">Upvotes</option>
    <option value="asc">Ascending</option>
    <option value="desc">Decending</option>
  </select>
  <button
    class="btn"
    @click="$emit('sort-by-dates')"
  >latest</button>
  <div
    class="hello"
    :key="article.title"
    v-for="article in articles"
  >
    <ArticleView
      class="box"
      :article="article"
    />
  </div>
</template>

<script>
import ArticleView from "./ArticleView.vue";

export default {
  name: "ArticleListPage",
  components: {
    ArticleView
  },
  data() {
    return {
      voteOrder: "-1"
    };
  },
  props: {
    articles: Array
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box {
  border-bottom: 1px solid #efefef;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
