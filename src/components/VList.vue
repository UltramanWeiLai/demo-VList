<template>
  <div class="th-vlist-wrapper" @scroll="handelScroll">
      <div class="th-vlist-scroll-bar" :style="{ height: `${scrollHeight}px` }"></div>
      <div class="th-vlist" :style="{ top: `${vListTop}px` }">
        <div class="th-vlist-row" v-for="(item, index) in _list" :key="index" >
          <p>{{ item.name }}</p>
        </div>
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue'

export default {
  name: 'VList',
  setup() {
    const list = ref([])
    const listItemHeight = ref(51)
    const showListNumber = ref(100)
    const startIndex = ref(0)
    const endIndex = ref(99)
    const scrollHeight = ref(0)
    const vListTop = ref(0)

    const _list = computed(() => list.value.slice(startIndex.value, endIndex.value))

    for (let i = 0; i < 10000; i++) {
      list.value.push({
        id: i,
        name: 'list:' + i
      })
    }

    scrollHeight.value = list.value.length * listItemHeight.value

    const handelScroll = (event) => {
      const scrollTop = event.target.scrollTop
      startIndex.value = Math.floor(scrollTop / listItemHeight.value)
      endIndex.value = startIndex.value + showListNumber.value
      vListTop.value = startIndex.value * listItemHeight.value
    }

    return {
      _list,
      startIndex,
      endIndex,
      scrollHeight,
      handelScroll,
      vListTop
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .th-vlist-wrapper {
    position: relative;
    width: 300px;
    height: 500px;
    margin: 0 auto;
    overflow-y: scroll;
    background-color: cornflowerblue;
  }

  .th-vlist {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    min-height: 10px;
  }

  .th-vlist-row {
    overflow: hidden;
    border-bottom: 1px solid white;
    box-sizing: border-box;
    background-color: tomato;
  }
</style>
