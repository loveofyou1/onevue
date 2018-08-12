<template>
  <div id="app">
    <!--<img src="./assets/logo.png">
    <view1></view1>
    <router-view/>-->
    <h1 v-text="title"></h1>
    <input v-model="newItem" v-on:keyup.enter="addNewItem"/>
    <ul>
      <li v-for="item in items" v-bind:class="{finished: item.isFinished}" v-on:click="toggleFinished(item)">
        {{item.label}}
      </li>
    </ul>
  </div>
</template>

<script>

  import store from './components/store'
  console.log(store)
  export default {
    name: 'App',
    data () {
      return {
        title: 'this is a todolist.',
        items: store.fetch(),
        newItem: ''
      }
    },
    watch:{
      items:{
        handler: function (items) {
          store.save(items)
        },
        deep: true
      }
    },
    methods:{
      toggleFinished: function (item) {
        item.isFinished = !item.isFinished
      },
      addNewItem: function(){
        this.items.push({
          label: this.newItem,
          isFinished: false
        })
        this.newItem = ''
        store.save(this.items)
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

  .finished {
    text-decoration: underline;
  }
</style>
