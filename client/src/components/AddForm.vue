<template>
    <div class="container my-5 py-3 border border-dark" style="width: 35%;">
        <div class="container" id="addTask">
            <form id="addTaskForm" v-on:submit.prevent="addTask">
                <div class="container">
                    <h3 class="text-center">Add a new task</h3>
                </div>
                <div class="form-group">
                    <label for="title">Title</label>
                    <input type="text" class="form-control" id="title" placeholder="Title" v-model="title">
                </div>
                <div class="form-group">
                    <label for="description">Description</label>
                    <textarea class="form-control" id="description" rows="3" placeholder="Provide a brief description." v-model="description"></textarea>
                </div>
                <div class="form-group">
                    <label for="category">Status</label>
                    <select class="form-control" style="width: 100%;" name="category" id="category" v-model="category">
                        <option>Select a status</option>
                        <option value="backlog">Backlog</option>
                        <option value="todo">Todo</option>
                        <option value="doing">Doing</option>
                        <option value="done">Done</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="assigned_to">Assigned to</label>
                    <input type="text" class="form-control" id="assigned_to" placeholder="e.g. Your or your colleague's name" v-model="assigned_to">
                </div>
                <button type="submit" class="btn btn-primary" style="width: 100%;">Add</button>
                <button type="button" class="btn btn-danger mt-1" style="width: 100%;" v-on:click.prevent="returnHome">Cancel</button>
            </form>
        </div>
    </div>  
</template>

<script>
export default {
    name: 'AddTaskForm',
    data(){
        return{
            page: 'add-page',
            title: '',
            description: '',
            category: '',
            assigned_to: ''

        }
    },
    methods:{
        returnHome(){
            this.$emit('changePage', 'home')
        },
        addTask(){
            console.log('masuk addTask method di addForm')
            let payload = {
                title: this.title,
                description: this.description,
                category: this.category,
                assigned_to: this.assigned_to
            }
            this.$emit('addTask', payload)
        }
    }
}
</script>

<style>

</style>