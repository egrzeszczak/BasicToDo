<template>
    <div 
    class="item"  
    :class="{ completed: item.completed }"
    >
        <div class="item-title">{{item.title}}</div>
        <button @click="completeTask" v-if="!item.completed">&#10003;</button>
      </div>
</template>

<script>
export default {
    props: ['item'],
    methods: {
        completeTask(){
            this.$emit('finishTask', this.item.id)
        }
    }
}
</script>

<style lang="scss">
    .item{
        transition: 1s width cubic-bezier(0.075, 0.82, 0.165, 1);
        margin-bottom: .5rem;
        border: 1px solid #c4c4c4;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
        display: grid;
        grid-template-columns: 1fr 50px;
        min-height: 52px;
        button{
          border: none;
          background: gainsboro;
          color: black;
          &:hover{
            background: rgb(163, 255, 163);
          }
        }
        .item-title{
          display: grid;
          align-items: center;
          text-align: left;
          padding-left: 3rem;
          transition: .25s padding ease-in;
        }
      }
      .completed{
        border: 1px solid rgb(163, 255, 163);
        background: rgb(163, 255, 163);
        color: black;
        transition: .25s background ease-in;
      }
</style>