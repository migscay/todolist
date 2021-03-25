<template>
    <div class="todoListContainer">
        <div class="heading">
            <h2 id="title">Todo List</h2>
            <AddItemForm 
                v-on:reloadList="getList()"    
            />
        </div>
        <ListView 
                :items="items"
            v-on:reloadList="getList()"    
             />
    </div>
</template>
    
<script>
    import AddItemForm from "./addItemForm"
    import ListView from "./listView"

    export default {
        name : "app",
        components: {
            AddItemForm,
            ListView
        },
        data: function () {
            return {
                items: []
            }
        },
        methods: {
            getList () {
                axios.get('api/items')
                .then( response => {
                    this.items = response.data
                })
                .catch (error => {
                    console.log(error);
                })
            }
        },
        created() {
            this.getList();
        }, 
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>

<style scoped>
.todoListContainer {
    width: 350px;
    margin: auto;
}

.heading {
    background: #e6e6e6;
    padding: 10px;
}

#title {
    text-align: center;
}
</style>