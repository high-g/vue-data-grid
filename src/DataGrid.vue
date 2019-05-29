<template>
  <div :class="gridType" :style="randomGridTemplates">
    <div
      v-for="(item, index) in list"
      :key="index"
      class="item"
      :style="randomGridArea(index + 1)"
    >
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
  data() {
    return {
      randomArray: [],
      randomColumnsMaxCount: 4
    }
  },
  computed: {
    /**
     * grid切り分け
     */
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
    },

    /**
     * ランダムgrid
     */
    randomGridTemplates() {
      let strTemplates = ''

      if(this.grid === 'random') {
        strTemplates = 'grid-template-areas:'
        const arr = this.randomArray

        for(let y=0; y<arr.length; y++) {
          if(arr[y].length > 0) {
            strTemplates += '"'
          }

          for(let x=0; x<this.randomColumnsMaxCount; x++) {
            if(arr[y][x]) {
              strTemplates += ' area' + arr[y][x]
            } else if(arr[y].length > 0) {
              strTemplates += ' .'
            }
          }

          if(arr[y].length > 0) {
            strTemplates += '" '
          }
        }
        strTemplates += ';'

        console.log(strTemplates);
      }

      return strTemplates
    },

    /**
     * ランダムgridArea
     */
    randomGridArea() {
      return (num) => {
        let strArea = ''

        if(this.grid === 'random') {
          strArea = 'grid-area: area' + num + ';';
          console.log('strArea',strArea)
        }
        return strArea
      }
    }
  },
  created() {
    if(this.grid === 'random') {
      this.createRandomArray(this.list.length)
    }
  },
  methods: {
    /**
     * 描画用二次元配列作成
     * @param len {Number}
     */
    createRandomArray(len) {
      let pos = {}
      let rect = {}

      for(let i = 1; i <= len; i++) {
        this.adjustRandomArray()
        pos = this.getRandomPosition()
        rect = this.getDrawRect(pos)
        this.setRandomArray(pos, rect, i)
      }
      console.log('randomArray', this.randomArray);
    },

    /**
     * 二次元配列格納領域調整
     */
    adjustRandomArray() {
      const arr = this.randomArray
      const len = arr.length
      let lastRow = 0

      // 値が入っている最終行を導く
      if(len === 0) {
        this.randomArray[0] = []
        this.randomArray[1] = []
      } else {
        for(let i=0; i<len; i++) {
          if(arr[i].length > 0) {
            lastRow = i;
          }
        }
        this.randomArray[lastRow + 1] = []
        this.randomArray[lastRow + 2] = []
      }
    },

    /**
     * 二次元配列格納領域調整
     */
    getRandomPosition() {
      const arr = this.randomArray
      const len = arr.length
      const max = this.randomColumnsMaxCount

      for(let y=0; y<len; y++) {
        for(let x=0; x<max; x++) {
          if(!arr[y][x]) {
            return {x, y}
          }
        }
      }
    },

    /**
     * 格納対象の縦横決定
     * @param pos {Object}
     */
    getDrawRect(pos) {
      return {
        w: (pos.x === this.randomColumnsMaxCount - 1) ? 1 : Math.floor((Math.random() * 2) + 1),
        h: Math.floor((Math.random() * 2) + 1)
      }
    },

    /**
     * 格納対象の縦横決定
     * @param pos {Object}
     * @param rect {Object}
     * @param num {Number}
     */
    setRandomArray(pos, rect, num) {
      this.randomArray[pos.y][pos.x] = num

      if(
        rect.w > 1 &&
        !this.randomArray[pos.y][pos.x + 1]
      ) {
        this.randomArray[pos.y][pos.x + 1] = num
      }
      if(
        rect.h > 1 &&
        !this.randomArray[pos.y + 1][pos.x]
      ) {
        this.randomArray[pos.y + 1][pos.x] = num
      }
      if(
        rect.w > 1 && rect.h > 1 &&
        !this.randomArray[pos.y + 1][pos.x + 1] &&
        this.randomArray[pos.y][pos.x + 1] === num &&
        this.randomArray[pos.y + 1][pos.x] === num
      ) {
        this.randomArray[pos.y + 1][pos.x + 1] = num
      }
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
