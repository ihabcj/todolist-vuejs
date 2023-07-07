<template>
    <div class="todolistContainer">
        <div class="heading">
            <h2 id="title">To Do List</h2>
            <add-item 
            v-on:reloadlist="getList()"
            />
        </div>
        <view-list 
        :items="items"
        v-on:reloadlist="getList()"/>
    </div>
</template>
   
<script>
import axios from 'axios';
import AddItem from './AddItem.vue';
import ViewList from './ViewList.vue'
export default {
    components: {
        AddItem,
        ViewList
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
                this.item = response.data
            })
            .catch (error => {
                console.log(error);
            })
        }
    },

    create()  {
        this.getList()
    }
}
</script>
   
<style scoped>
.todolistContainer{
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