
<template>
      <h1>Counter - vueX Conocimientos basicos </h1>
    <h2> Direct acces: {{ $store.state.counter.count }}</h2>
    <h2> computed: {{ countComputed }}</h2>

  <button @click="incrementar"> +1</button>
    <button  @click="incrementarPor"> +5</button>
   <button   @click="incrementRandomInt" :disabled="isLoading">Random</button>
      <!-- <button   @click="randomInt" > Random</button> -->
<h1>mapState</h1>
<h2>mapState VIDEO 143:{{count}} </h2>
<h3> last mutation 143: {{lastMutation}}</h3>
<h2>Direct getter: {{$store.getters['counter/squareCount']}}</h2>
</template>



<script>
import {mapState, mapActions } from 'vuex'


export default {

// computed: mapState(['count'])

computed: {
    countComputed(){
      return this.$store.state.counter.count
    },
    ...mapState('counter',['count', 'lastMutation', 'isLoading'])
    // ...mapState({
    //   count: state => state.count,
    //   lastMutation: state =>state.lastMutation
    // })
  },

  methods:{
    incrementar(){
      this.$store.commit('counter/increment')
    },
    incrementarPor(){
      this.$store.commit('counter/incrementBy', 5)
      // this.randomInt()
    },
    // incrementarRandom(){
    //     this.$store.dispatch('incrementRandomInt', 2)
    // },
    ...mapActions('counter', ['incrementRandomInt'])
        // ...mapActions(''counter,{
        //   randomInt: 'incrementRandomInt'
        //   })
  }

}
</script>