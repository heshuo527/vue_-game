<template>
  <div>
    <div class="hs-container" @click="onClickCell">
      <template v-if="a">{{text}}</template>
      <template v-else>{{ text}}</template>
    </div>
  </div>
</template>

<script>
export default {
  props: ['n'],
  data() {
    return { a: false, text: '' }
  },
  methods: {
    onClickCell() {
      if (this.text !== "") {
        return
      }
      this.a = true
      this.text = this.n % 2  === 0 ? "x" : "o"
      this.$emit("click", this.text)
    }
  }
}

</script>

<style scoped>
.hs-container {
  border: 1px solid red;
  width: 100px;
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 80px;
}
</style>
