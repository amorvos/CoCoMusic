<template>
  <div>
    <div class="album-list">
      <div class="album-item" v-for="(item,index) in list.list" :key="index">
        <router-link :to="`/album/${item.albumMid}`">
          <img v-lazy="`https://y.gtimg.cn/music/photo_new/T002R300x300M000${item.albumMid}.jpg`">
          <p>{{item.albumName}}</p>
        </router-link>
      </div>
    </div>
    <div v-if="!hideMoreBtn">
      <button class="more btn btn-block" @click="$emit('next')" v-show="!list.isEnd" :class="{'loading':list.isLoading}">More</button>
      <div class="divider text-center" v-show="list.isEnd" data-content="没有了"></div>
    </div>
  </div>
</template>
<script>
export default {
  props: ['list', 'hideMoreBtn']
}
</script>
<style lang="stylus" scoped>
.album-list
    display flex
    flex-wrap wrap
.album-item
  width 150px
  text-align center
  img
    width 130px
    height 130px
    border-radius 6px
  p
    white-space nowrap
    overflow hidden
    text-overflow ellipsis
</style>
