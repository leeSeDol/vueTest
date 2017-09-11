<template>
    <div id="app">
        <h1 v-html="title">{{title}}</h1>
        <input type="text" v-model="newItem" v-on:keyup.enter="addNew">
        <ul>
            <li v-for="item in items" v-bind:class=" { finish: item.isFinished}" v-on:click="toggleFinish(item)">
                {{item.label}}
            </li>
        </ul>
    </div>
</template>

<script>
import Store from './store.js'
console.log(Store);
export default {
    data:function(){
        return {
            title:' this is todo list <span>!</span>',
            items: Store.fetch() ,
            newItem : ''
        }
    },
    watch:{
        items:{
            handler:function(items){
                Store.save(items);
            },
            deep:true
        }  

    },
    methods:{
        toggleFinish:function(item){
            item.isFinished = !item.isFinished;
        },
        addNew:function(){

            this.items.unshift({
                label: this.newItem ,
                isFinished : false
            });
            this.newItem = '';
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
