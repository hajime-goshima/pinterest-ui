<template>
  <section class="container">
    <button class="back-to" @click="backTo">←</button>
    <div class="item-detail">
      <h1>{{ item.id }}: {{ item.title }}</h1>
      <p>{{ item.body }}</p>
    </div>
    >
    <button class="back-to" @click="backTo">←</button>
  </section>
</template>

<script>
export default {
  data() {
    return {
      item: {
        id: '',
        title: '',
        body: ''
      }
    }
  },
  asyncData({ app, route }) {
    const data = {}
    data.item = {
      id: route.params.id,
      title: `Title${route.params.id}`,
      body: `Body${route.params.id}`
    }
    return data
  },
  methods: {
    backTo() {
      this.$router.back()
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
}

.item-detail {
}

.back-to {
  display: block;
  padding: 15px 50px;
  font-size: 18px;
  background: orange;
  margin: 15px 0;
}
</style>
