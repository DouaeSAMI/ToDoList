<template>
    <div>
        <h2>{{todo.title}}</h2>
        <div class="d-flex justify-content-end">
            <button class="btn btn-info">Edit</button> 
            <button class="btn btn-danger" @click="deleteTodo(todo.id)" >Delete</button>
        </div>
    </div>
</template>

<script>
export default
{
    props: ['todo'],
    methods:
    {
        deleteTodo(){
            this.$emit('deleteTodo',this.todo.id);
        }
    }
}
</script>