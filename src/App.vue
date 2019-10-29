<template>
  <div id="app">
    <h1 class="title">DuMbIfY wRiTtInG</h1>
    <textarea class="text-area" v-model="phrase"></textarea>
    <br/>
    <button @click="dumbify" class="button">DUMBIFY!</button>
    <p>{{ dumbPhrase }}</p>
  </div>
</template>

<script>

export default {
  name: 'app',
  data() {
    return {
      phrase: '',
      dumbPhrase: ''
    }
  },
  methods: {
    dumbify() {
      let splited = this.phrase.toLowerCase().split(' ')
      let accumulator = ''
      splited.forEach(word => {
        let splitedWord = word.split('')
        for (let i = 0; i < splitedWord.length; i++) {
          if (i % 2 === 0) {
            accumulator += splitedWord[i].toUpperCase()
          } else {
            accumulator += splitedWord[i]
          }
        }
        accumulator += ' '
      })
      this.dumbPhrase = accumulator
    }
  }
}
</script>

<style lang="scss" scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.title {
  text-align: center;
}

.button {
  border: none;
  background-color: #252525;
  border-radius: 10px;
  padding: 10px 15px;
  color: white;
  cursor: pointer;
  margin-top: 15px;

  &:hover {
    opacity: .8;
  }
}

.text-area {
  height: 40vh;
  width: 50%;
}
</style>
