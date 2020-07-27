<template>
  <div id="app">
    <Header></Header>
    <PageList
        v-on:mainSelect="mainSelect"
    ></PageList>
<!--    <img alt="Vue logo" src="./assets/logo.png">-->
    <Main v-bind:key="pages.title" v-bind:title="pages.title" v-bind:abstract="pages.abstract"></Main>
  </div>
</template>

<script>
    // import Main from "@/components/Main";
    import Header from "@/components/Header";
    import PageList from "@/components/PageList";
    import Main from "@/components/Main"

    export default {
        name: 'App',
        components: {
            PageList,
            Header,
            Main
        },
        data: function () {
            return{
                pages:Object
            }
        },
        methods:{
            mainSelect(contents){
                this.pages = contents;
            }
        }

    }
</script>

<style lang="scss">
  body{
    margin: 0;
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    padding-top: 2em;
    margin: 0;
    display: flex;
    #mainPages{
      width: 100%;
    }
  }
</style>
