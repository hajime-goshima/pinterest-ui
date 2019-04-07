<template>
  <section class="container">
    <div class="welcome">
      <h1 class="title">
        Pinterest-UI
      </h1>
      <h2 class="subtitle">
        Nuxt.jsでPisterestのようなページ遷移を実装する
      </h2>
      <div class="arrow"></div>
    </div>
    <div
      v-for="item in items"
      :key="item.id"
      class="item-list"
      :to="`/${item.id}`"
      @click="showDetail(item)"
    >
      <div class="item">
        <h3>{{ item.title }}</h3>
        <p>{{ item.body }}</p>
      </div>
    </div>
    <button class="readmore" @click="readMore">もっと読み込む</button>
    <div v-if="isShowDetail" class="detail-page-wrapper">
      <Item :item="detailItem" />
    </div>
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
      detailItem: null,
      isShowDetail: false,
      items: [
        { id: 1, title: 'Title1', body: 'Body1' },
        { id: 2, title: 'Title2', body: 'Body2' },
        { id: 3, title: 'Title3', body: 'Body3' }
      ]
    }
  },
  methods: {
    readMore() {
      const length = this.items.length
      for (let i = 1; i <= 3; i++) {
        const id = length + i
        this.items.push({ id: id, title: `Title${id}`, body: `Body${id}` })
      }
    },
    async showDetail(item) {
      // 初期化
      this.detailItem = null

      // データの取得
      // axiosやgraphql query等
      const self = this
      await setTimeout(function() {
        self.detailItem = item
        self.isShowDetail = true
        window.history.pushState('detail-page', `/${item.id}`, `/${item.id}`)
      }, 1000)
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
}

.welcome {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.arrow {
  position: absolute;
  bottom: 50px;
  border-right: #7f828b 3px solid;
  border-bottom: #7f828b 3px solid;
  height: 50px;
  width: 50px;
  transform: rotate(45deg);
}

.item-list {
  text-decoration: none;
}
.item-list .item {
  border: 1px solid #ddd;
  padding: 50px;
  margin-bottom: 15px;
  cursor: pointer;
}
.item-list .item h3 {
  font-size: 30px;
}
.item-list .item p {
  padding-top: 15px;
}

.readmore {
  display: block;
  padding: 15px 50px;
  font-size: 18px;
  background: orange;
  margin: 15px auto;
}

.detail-page-wrapper {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  max-height: 100vh;
  background: rgba(50, 50, 50, 0.5);
}
</style>
