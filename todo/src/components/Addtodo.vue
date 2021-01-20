<template>
<form  @submit.prevent="addtodo">
    <input type="text" v-model="title" name="title" id="" placeholder="Enter your todo">
    <input type="submit" class="btn" value="Submit">
</form>
</template>

<script>

export default {
    name:"Addtodo",
    data(){
        return{
            title:""
        }
    },

    methods:{
        addtodo(){
          const newtodo={
          title: this.title,
          completed:false
          }

         this.$emit("add-todo", newtodo)

         this.title=""

        }
        

       

    }


}

</script>

<style scoped>
form {
    display: flex;
    
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
    outline: none;
  }
  input[type="submit"] {
    flex: 2;
  }


</style>