<template>
    <div>
        <div v-for="(item, index) in items" :key="index">
            <items-list
                :item="item"
                class="item"
                v-on:itemchanged="$emit('reloadlist')"
                />
        </div>
    </div>
</template>
   
<script>
import ItemsList from './ItemsList.vue';
export default {
    props: ['items'],
    components: {
        ItemsList
    }
}
</script>
   
<style scoped>
.item {
    background: #e6e6e6;
    padding: 5px;

}
</style>
   