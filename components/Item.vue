<template>
  <section class="container-wrapper">
    <div class="container">
      <button class="back-to" @click="backTo">←</button>
      <div class="item-detail">
        <h1>{{ item.id }}: {{ item.title }}</h1>
        <p>{{ item.body }}</p>
      </div>
      <button class="back-to" @click="backTo">←</button>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    item: Object
  },
  methods: {
    backTo() {
      this.$router.back()
    }
  }
}
</script>

<style scoped>
.container-wrapper {
  width: 100%;
  height: 100vh;
  max-height: 100vh;
}
.container {
  max-width: 800px;
  margin: 0 auto;
  background: white;
}

.item-detail {
  padding: 30px;
}

.back-to {
  display: block;
  padding: 15px 50px;
  font-size: 18px;
  background: orange;
  margin: 15px 0;
}
</style>
