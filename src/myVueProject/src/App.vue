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
    <p>child say {{childrentell}}</p>
    <HelloWorld/>
    <componentA msgfromfather='father' @childrentell="listentomyson"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Store from './store';
import componentA from './components/componentA'
console.log(Store);
export default {
  name: 'App',
  components: {
    HelloWorld,componentA
  },

  data:function(){
    return {
       title: '<span>2018-11-5：</span>TODOList',
       items:Store.fetch(),
       liclass:'thisisliclass',
       newItem:'',
       childrentell:''
    }
  },

  watch:{
     items: {
      handler: function (items) { 
        Store.save(items);
      },
      deep: true
    },
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
    },
    listentomyson:function(msg){
      // alert();
      this.childrentell = msg;
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
