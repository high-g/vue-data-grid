<template>
  <div class="grid">
    <div v-for="(item, index) in list" :key="index" class="item">
      <img :src="item.img">
      <p>{{ item.text }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    list: Array
  },
  computed: {
    gridType(type) {
      switch(type) {
        case 'normal':
          return ''
        case 'random':
          return ''

      }
    }
  }
}
</script>

<style lang="scss" scoped>
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 30px;

  img {
    width: 100%;
  }
}
</style>
