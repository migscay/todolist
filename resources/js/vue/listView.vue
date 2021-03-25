<template>
    <div>
        <div v-for="(item,index) in items" :key="index" >
            <ListItem 
                :item="item"
                class="item"
                v-on:itemChanged="$emit('reloadList')"    
            />
        </div>    
    </div>
</template>

    
<script>
    import ListItem from "./listItem"
    
    export default {
        props: ['items'],
        components: {
            ListItem
        },
        name : "listView",
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>

<style scoped>
.item {
    background: #e6e6e6;
    padding: 5px;
    margin-top: 5px;
}
</style>