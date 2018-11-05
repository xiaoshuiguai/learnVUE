<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1 v-html='title'></h1>
    <input v-model="newItem" v-on:keyup.enter="addNew">
    <ul>
      <li  v-for="item in items" :class="{finished:item.isFinished}" v-on:click="aaaaa(item)">
        {{item.label}}
      </li>
    </ul>
    <HelloWorld/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data:function(){
    return {
       title: '<span>2018-11-5：</span>TODOList',
       items:[
        
       ],
       liclass:'thisisliclass',
       newItem:''
    }
  },
  methods:{
    aaaaa:function(a){
      a.isFinished=!a.isFinished
      console.log(a);
    },
    addNew:function(){
      console.log(this.newItem);
      this.items.push({
        label:this.newItem,
        isFinished:false
      })
      this.newItem = '';
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
.finished{
  text-decoration: underline;
}
</style>
