<template>
<div id="app">
<img alt="Vue logo" src="./assets/logo.png">
<input v-model="num" @input="countersInit">
<!-- <Counter msg = "" v-for="n in parseInt(num)" v-bind:key = "n" v-bind:index = "n"/> -->
<Counter msg = "" v-for="n in getNum()" v-bind:key = "n" v-bind:index = "n" v-bind:counter="counters[n-1]" v-on:update="getValueFromChild"/>
<p>{{sum}}</p>

</div>
</template>

<script>
import Counter from './components/Counter.vue'

export default {
name: 'app',
components: {
Counter
},

data(){
return {
      num:0,
      counters:[],
      sum:0
}
},


methods:{

isNumber(n){
  return !isNaN(parseInt(n)) && isFinite(n);
},

countersInit(){
                this.counters=[];
                if(this.isNumber(this.num)){
                    for(let i=1; i<=this.num; i++){
                        this.counters.push(i);
                    }
                }
                this.getSum();
            },

getNum: function (){
  if(this.isNumber(this.num)){
                    return parseInt(this.num);
                }else {
                    this.num = 0;
                    this.sum = 0;
                    return this.num;
                }
},

getValueFromChild(data){
  this.counters[data.index-1] = data.value;
  this.getSum();
},

getSum(){
  this.sum = 0;
  for(let i=0; i<this.counters.length;i++){
  this.sum+=this.counters[i];
        }
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