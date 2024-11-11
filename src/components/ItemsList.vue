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
    }
}
</script>

<style lang="scss" scoped>
.items-list {
    margin-top: 25px;
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
    border-radius: 5px;
}
</style>