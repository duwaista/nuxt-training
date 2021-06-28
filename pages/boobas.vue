<template class="feed-root">
  <div class="feed-list">
    <h1><span>Ah shit, here we go again</span></h1>
    <div v-for="feed in all" :key="feed._id"  class="feed-container">
        <img class="feed-image" :src="feed.posts" />
    </div>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      all: [{}],
    }
  },
  created() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start()
    })
  },
  mounted() {
    this.getData();
  },
  methods: {
    getData() {
      fetch('https://quiet-ridge-83792.herokuapp.com/api/feed/', {
        method: 'GET',
      }).then(async (response) => {
        this.all = await response.json();
        this.all.reverse();
        this.$nuxt.$loading.finish();
      })
    },
  },
}
</script>

<style scoped>
.feed-list {
    display: flex;
    width: 100%;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.feed-container {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    position: relative;
    width: 500px;
    height: 300px;
    border-radius: 8px;
    box-shadow: 0 0 3px rgba(0, 0, 0, 0.4);
    margin-bottom: 6px;
}
.feed-image {
    position: relative;
    width: 98%;
    height: 96%;
    object-fit: cover;
}
</style>
