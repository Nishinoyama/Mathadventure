<template>
<!--  title, abstract, contents-->
  <div class="pageListing">
    <li v-on:click="mainSelect(contents)">{{contents.title}}</li>
    <ul v-if="contents.contents" v-once>
      <PageListing
          v-for="item in contents.contents" v-bind:key="item.title"
          v-bind:contents="item"
          v-on:mainSelect="mainSelect"
      ></PageListing>
    </ul>
  </div>
</template>

<script>
    export default {
        name: "PageListing",
        props:{
            contents:Object
        },
        methods:{
            mainSelect(contents){
                this.$emit('mainSelect', contents );
            }
        }
    }
</script>

<style scoped>
  ul{
    padding-left: 1ch;
    font-size: 0.85em;
    list-style-type: none;
  }
  li:hover{
    background-color: #40586f;
    cursor: pointer;
  }
</style>