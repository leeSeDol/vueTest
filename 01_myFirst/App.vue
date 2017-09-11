<template>
    <div id="app">
        <h1 v-html="title">{{title}}</h1>
        <ul>
            <li v-for="item in items" v-bind:class=" { finish: item.isFinished}" v-on:click="toggleFinish(item)">
                {{item.label}}
            </li>
        </ul>
    </div>
</template>

<script>


export default {
    data:function(){
        return {
            title:'<span>?</span>this is todo list2',
            items:[
                {
                    label:'coding',
                    isFinished:false
                },
                {
                    label:'walking',
                    isFinished:true
                }
            ]
        }
    },
    methods:{
        toggleFinish:function(item){
            item.isFinished = !item.isFinished;
        }
    }
}
</script>

<style>
*{
    margin:0;
    padding:0;
    list-style-type:none;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.finish{
    text-decoration:underline;
}
</style>
