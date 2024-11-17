<template>
<div class="items-list">
    <ListItem v-for="item in items" :key="item" :item="item"/>
</div>
</template>
<script>
import ListItem from './ListItem.vue';
export default {
    props: {
        items: []
    },
    components: {
        ListItem
    },
}
</script>

<style lang="scss" scoped>
.items-list {
    margin-top: 25px;
    border-radius: 5px;
}
</style>