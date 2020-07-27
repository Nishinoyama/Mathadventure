<template>
  <div id="PageList">
    <ul>
      <PageListing
          v-for="item in pageList" v-bind:key="item.title"
          v-bind:contents="item"
          v-on:mainSelect="mainSelect"
      ></PageListing>
    </ul>
  </div>
</template>

<script>
    import PageListing from "@/components/PageListing";
    export default {
        name: "PageList",
        components: {PageListing},
        data: function () {
            return{
                pageList:[]
            }
        },
        mounted() {
            this.pageList = require("@/assets/db/contents");
        },
        methods:{
            mainSelect(contents){
                this.$emit('mainSelect', contents );
            }
        }

    }
</script>

<style lang="scss">
  #PageList{
    text-align: left;
    display: block;
    width: 240px;
    background-color: #2c3e50;
    color: #e2ffef;
    height: calc(100vh - 2rem);
    top: 2em;
    position: sticky;
    overflow-y: scroll;
  }
  ul{
    font-size: 1.3em;
    padding-left: 1ch;
    list-style-type: none;
  }
  // スマートフォンサイズ
  // @media screen and (max-width: 768px){
  //   #PageList{
  //     display: none;
  //   }
  // }
</style>