<template>
  <div class="to-dolist">
    <div class="input-box">
      <input type="text" id="input" v-model="todoData" />
      <button type="submit" @click="addList">
        <span class="button-text"> Add Todo List </span>
      </button>
    </div>
    <ul>
      <li v-for="i in item" :key="i" class="list">
        <div class="add-list">
          <span class="list-data">{{ i }}</span>
          <button @click="removeItem(i)"><span>Remove</span></button>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "todoList",
  data() {
    return {
      todoData: "",
      item: [],
    };
  },
  methods: {
    addList() {
      if (this.todoData) {
        this.item.push(this.todoData);
        console.log(this.item);
      }
    },
    removeItem(data){
     let dataItem= this.item.filter(it=>{
        return it.toLowerCase() != data.toLowerCase()
      })
      this.item=dataItem

    }
  },
};
</script>
<style lang="less">
body{
  background-color: rgb(227, 227, 168);
}
.to-dolist {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  .input-box {
    input {
      width: 300px;
      height: 20px;
      padding: 10px;
      border-radius: 3px;
      border: 2px solid rgb(98, 227, 98);
    }
    input:hover {
      border: 2px solid red;
    }
    button {
      width: 150px;
      height: 30px;
      border: 2px solid rgb(217, 207, 207);
      background-color: rgb(37, 35, 35);
      margin: 10px;
      cursor: pointer;
      .button-text {
        color: white;
        padding: 10px;
      }
    }
  }
  ul {
    list-style-type: none;
    .list {
      display: flex;
      flex-direction: column;
      margin-top:10px;
      .add-list{
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        .list-data {
        background-color: rgb(228, 188, 188);
        border: 1px solid red;
        border-radius: 4px;
        padding:5px;
        color:red
      }
      button {
        margin-left: 20px;
        width: px;
        height: 30px;
        background-color: red;
        cursor: pointer;
        span {
          padding: 10px;
          color: white;
          padding:10px;
        }
      }
      }
    
    }
  }
}
</style>
