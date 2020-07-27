<template>
  <div class="Header">
    <transition>
      <h1 v-show="show" v-text="title"></h1>
    </transition>
  </div>
</template>

<script>
    export default {
        name: "Header",
        props: {
        },
        data: function() {
            return {
                title: "Mathadventure",
                show: false,
            };
        },

        mounted() {
            this.show = true;
        },
    }
</script>

<style scoped lang="scss">
  *{
    margin: 0;
  }
  .Header{
    background-color: #42b983;
    display: block;
    width: 100vw;
    height: 2em;
    margin: 0;
    top: 0;
    .half_block{
      width: 50%;
      height: 100%;
      overflow: hidden;
      float: left;
      li{
        font-size: 1em;
      }
    }
    h1{
      margin: 0;
      font-size: 2em;
    }
    position: fixed;
  }

  .v-enter-active, .v-leave-active{
    transition: opacity 600ms ease-out;
  }

  .v-enter, .v-leave-to{
    opacity: 0;
  }

</style>