<template>
    <div>
        <form @submit.prevent='handleAdd'>
            <input v-model='itemTitle' placeholder='Add Item' type="text" class='input'>
            <button type='submit' value='submit' class='button'>Add</button>
        </form>
    </div>
</template>

<script>
export default {
    data() {
        return {
            itemTitle: ''
        }
    },
    methods: {
        handleAdd(){
            const newTodo = {
                title: this.itemTitle,
                complete: false
            }
            this.$emit('add-todo', newTodo)
            this.itemTitle = ''
        }
    }
}
</script>

<style>
    .input{
        border: none;
        background: lightgrey;
        border-radius: 3px;
        height: 20px;
        width: 75%;
    }
    .button{
        border: none;
        height: 20px;
        background: #4776a5;
        border-radius: 2px;
        color: whitesmoke;
        margin-left: 2px;
    }
    form{
        margin-top: 15px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>


