<template>
  <div>
    <p>click {{$store.state.count}} times, count is {{evenOrOdd}}</p>

    <button @click="increment">+</button>
    <button @click="decrement">-</button>
    <button @click="incrementIfOdd">increment if odd</button>
    <button @click="incrementAsync">increment async</button>
  </div>
</template>

<script>
  export default {
    name: 'App',
    computed: {
      evenOrOdd () {
        return this.$store.getters.evenOrOdd
      }
    },
    methods: {
      increment () {
        // 法一：
        // const count = this.count
        // this.count = count + 1
        // 法二：
        this.$store.dispatch('increment') // 触发store对应的action执行，名字相同的方法
      },
      decrement () {
        // const count = this.count
        // this.count = count - 1

        this.$store.dispatch('decrement')
      },
      incrementIfOdd () {
        // const count = this.count
        // if (count % 2 === 1) {
        //   this.count = count + 1
        // }
        this.$store.dispatch('incrementIfOdd')
      },
      incrementAsync () {
        // setTimeout(() => {
        //   const count = this.count
        //   this.count = count + 1
        // }, 1000)

        this.$store.dispatch('incrementAsync')
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
