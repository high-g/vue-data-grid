<template>
  <div :class="gridType">
    <div v-for="(item, index) in list" :key="index" class="item">
      <img :src="item.img">
      <p>{{ item.text }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    list: Array,
    grid: String
  },
  computed: {
    gridType() {
      const grid = this.grid
      if(
        grid === 'normal' ||
        grid === 'masonry' ||
        grid === 'random'
      ) {
        return grid
      } else {
        return 'normal'
      }
    }
  },
  mounted() {
    console.log('this.list',this.list)
    if(this.grid === 'random') {
      console.log(1)
    }
  }
}
</script>

<style lang="scss" scoped>
.item {
  padding: 5px;
  border-radius: 5px;
  border: 1px solid #999;

  img {
    width: 100%;
  }
}

.normal {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  column-gap: 5px;
  row-gap: 5px;
}

.masonry {
  column-count: 3;
  column-gap: 3px;

  .item {
    page-break-inside: avoid;
    break-inside: avoid;
    margin-bottom: 3px;
  }
}

.random {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  column-gap: 5px;
  row-gap: 5px;
}

@media (max-width: 800px) {
  .normal {
    grid-template-columns: 1fr 1fr;
  }
  .masonry {
    column-count: 2;
  }
}

@media (max-width: 480px) {
  .normal {
    grid-template-columns: 1fr;
  }
  .masonry {
    column-count: 1;
  }
}
</style>
