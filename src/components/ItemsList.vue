<template>
<div class="items-list">
    <ListItem v-for="item in items" :key="item" :item="item" @remove="itemRemoved" @item-checked="itemChecked"/>
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
        itemRemoved(item) {
            this.$emit('removal', item)
        },
        itemChecked(item) {
            this.$emit('checked', item)
        }
    }
}
</script>

<style lang="scss" scoped>
.items-list {
    margin-top: 25px;
    border-radius: 5px;
}
</style>