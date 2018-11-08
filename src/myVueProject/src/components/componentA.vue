<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{ msgfromfather }}</h1>
    <button @click="clickme">Click</button>
    <button @click="clickme2">Click</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data :function() {
    return {
      msg: this.msgfromfather
    }
  },
  props:['msgfromfather'],
  methods:{
    clickme:function(){
      alert(this.msgfromfather);
    },
    clickme2:function(){
      this.$emit("childrentell",this.msg);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
