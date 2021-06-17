<template>
  <div class="list">
    <ul v-for="post in posts">
      <row :post="post" @handler="remove"></row>
    </ul>
  </div>
</template>

<script>

import axios from 'axios'
import Row from '../components/Row';

export default {
  name: "List",
  components: {
    Row
  },
  data() {
    return {
      posts: {},
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/posts').then((response) => {
      this.posts = response.data
    });
  },
  methods: {
    remove(id) {
      this.posts = this.posts.filter(function (item) {
        return item.id !== id
      })
    }
  }
}
</script>

<style scoped lang="scss">
ul {
  list-style-type: none;

  li {
    text-align: left;
  }
}
</style>