<template>
<div class="items-list">
    <ListItem v-for="item in items" :key="item" :item="item"/>
</div>
</template>
<script>
import ListItem from './ListItem.vue';
export default {
    data() {
        return {
          
        }
    },
    props: {
        items: []
    },
    components: {
        ListItem
    },
    methods:{
        // itemChecked(item) {
        //     this.$emit('checked', item)
        // }
    }
}
</script>

<style lang="scss" scoped>
.items-list {
    margin-top: 25px;
    border-radius: 5px;
}
</style>