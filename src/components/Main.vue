<template>
  <div class="Main">
    <div class="header">
      <h1>{{title}}</h1>
    </div>
    <div class="abstract">
      <h2>概要</h2>
      <p>{{abstract}}</p>
    </div>
  </div>
</template>

<script>
    export default {
        name: "Main",
        props: {
            title: String,
            abstract: String
        }
    }
</script>

<style scoped lang="scss">
  *{
    margin: 0
  }

  .Main {
    text-align: left;
    width: 100%;
    max-width: 800px;
    margin-top: 1em;
    margin-left: auto;
    margin-right: auto;
    padding: 0 5px;
    display: block;
    .abstract {
      font-size: 1em;
    }
    .header {
      height: auto;
      font-size: 1.2em;
      color: #e2ffef;
      background-color: #42b983;
    }
  }
</style>