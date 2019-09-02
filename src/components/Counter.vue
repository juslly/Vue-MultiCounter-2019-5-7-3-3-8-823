<template>
<div class="hello">
<span>{{ index }}</span>
<button type="button" v-on:click="_add">+</button>
<span>{{counter}}</span>
<button type="button" v-on:click="_minus">-</button>
</div>
</template>

<script>
export default {
name: 'Counter',
props: {
index: Number,
msg: String,
counter:Number
},

data(){
return {
counterInChild: this.counter
}
},
methods:{
_add: function (){
    this.counterInChild ++;
     this.returnCounter();
},

_minus: function (){
this.counterInChild --;
 this.returnCounter();
},
 returnCounter(){
                this.$emit('update',
                    {
                        index:this.index,
                        value:this.counterInChild
                      }
                );
            }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
margin: 40px 0 0;
}
ul {
list-style-type: none;
padding: 0;
}
li {
display: inline-block;
margin: 0 10px;
}
a {
color: #42b983;
}
</style>