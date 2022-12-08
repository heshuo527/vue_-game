<template>
  <div id="app">
    <h3>第{{ n }}手</h3>
    <div class="row">
      <HelloWorld @click="handleOnClick(0, $event)" :n="n" />
      <HelloWorld @click="handleOnClick(1, $event)" :n="n" />
      <HelloWorld @click="handleOnClick(2, $event)" :n="n" />
    </div>
    <div class="row">
      <HelloWorld @click="handleOnClick(3, $event)" :n="n" />
      <HelloWorld @click="handleOnClick(4, $event)" :n="n" />
      <HelloWorld @click="handleOnClick(5, $event)" :n="n" />
    </div>
    <div class="row">
      <HelloWorld @click="handleOnClick(6, $event)" :n="n" />
      <HelloWorld @click="handleOnClick(7, $event)" :n="n" />
      <HelloWorld @click="handleOnClick(8, $event)" :n="n" />
    </div>
    <h3>{{ (result === null ? '胜负未分' : `胜方为${result}`) }}</h3>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Index from './components/index.vue'

export default {
  name: 'App',
  data() {
    return {
      n: 0,
      map: [
        [null, null, null],
        [null, null, null],
        [null, null, null]
      ],
      result: ''
    }
  },
  components: {
    HelloWorld,
    Index
  },
  methods: {
    handleOnClick(i, text) {
      this.n += 1,
        this.map[Math.floor(i / 3)][i % 3] = text,
        this.tell()
      console.log('点击的序号是', i, '内容是', text);
    },
    tell() {
      const map = this.map
      for (let i = 0; i < 2; i++) {
        if (
          map[i][0] !== null &&
          map[i][0] === map[i][1] &&
          map[i][1] === map[i][2]
        ) {
          this.result = map[i][0]
          setTimeout(() => {
            alert(`${this.result}赢了`)
          }, 100);
        }
      }
      for (let j = 0; j < 2; j++) {
        if (
          map[0][j] !== null &&
          map[0][j] === map[1][j] &&
          map[1][j] === map[2][j]
        ) {
          this.result = map[0][j]
          setTimeout(() => {
            alert(`${this.result}赢了`)
          }, 500);
        }
      }
      if (
        map[0][0] !== null &&
        map[0][0] === map[1][1] &&
        map[1][1] === map[2][2]
      ) {
        this.result = map[0][0]
        setTimeout(() => {
          alert(`${this.result}赢了`)
        }, 500);
      }
      if (
        map[0][2] !== null &&
        map[0][2] === map[1][1] &&
        map[1][1] === map[2][0]
      ) {
        this.result = map[0][2]
        setTimeout(() => {
          alert(`${this.result}赢了`)
        }, 500);
      }
    }
  }
}
</script>

<style>
.row {
  display: flex;
}
</style>
