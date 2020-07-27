<template>
  <div id="Test">
    <div v-on:click="handler('div1')">
      div1
      <a href="#Test" v-on:click.stop="handler('div2')">div2</a>
    </div>
    <h2>モンスターの追加</h2>
    <input v-model="name"> <input v-model.number="hp"><br>
    <button v-on:click="doAddMonsterToList">追加</button><br>
    <button v-on:click="handleClick($event)">TEST</button>
    <ul>
      <li v-for="(monster, index) in monsterList" v-bind:key="monster.id">
        ID.{{ monster.id ? monster.id : index }} {{ monster.name }} <span v-bind:class="{low: monster.hp < 30}"> HP.{{ monster.hp }} </span>
        <button v-on:click="doRemoveMonsterFromList(index)">削除</button>
        <button v-on:click="doAttackMonster(index)">攻撃</button>
      </li>
    </ul>
  </div>
</template>

<script>

    // import axios from 'axios'

    export default {
        name: "Test",
        data: function () {
            return{
                name:'name',
                hp:300,
                monsterList:[]
            }
        },

        created(){
            this.monsterList = require("../assets/db/monsterList");
        },

        methods: {
            doAddMonsterToList(){
                let id = this.monsterList.reduce((a,b)=> a>b.id?a:b.id, 0) + 1;
                this.monsterList.push({
                    id:id,
                    name:this.name,
                    hp:this.hp
                })
            },
            doRemoveMonsterFromList(index){
                this.monsterList.splice(index,1);
            },
            doAttackMonster(index){
                this.monsterList[index].hp -= 10;
                if ( this.monsterList[index].hp <= 0 ){
                    this.doRemoveMonsterFromList(index);
                }
            },
            handleClick(event){
                alert(event)
            },
            handler(str){
                console.log(str);
            }
        }
    }
</script>

<style scoped lang="scss">
  #Test {
    text-align: left;
    width: 100%;
    max-width: 800px;
    margin-top: 3em;
    margin-left: auto;
    margin-right: auto;
    display: block;
    background-color: #4ff7b5;
    .low{
      color: #b9326d;
    }
  }
  h2{
    margin: 0;
  }


</style>