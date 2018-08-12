<template>
    <div>
      <h1>view1</h1>
      <h2>this is view1.</h2>
      <h3>{{msg}}</h3>
      <h4>{{msg2}}</h4>
    </div>
</template>

<script>
export default {
  name: 'view1',
  data () {
    return {
      msg: 'hello world',
      msg2: 'hello hell'
    }
  }
}
</script>

<style scoped>

</style>
