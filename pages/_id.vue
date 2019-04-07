<template>
  <section class="container">
    <Item :item="item" />
  </section>
</template>

<script>
import Item from '@/components/Item.vue'
export default {
  components: {
    Item
  },
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
