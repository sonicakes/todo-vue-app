<template>
    <div class="item-circle-wrapper">
        <div class="item-circle">{{ item }}</div>
        <div class="circle"></div>
    </div>
</template>
<script>
export default {
    data() {
        return {

        }
},
props: {
    item:  {
    type: String,
    required: true
}
}
}
</script>
<style lang="scss" scoped>
@import '../styles/style.scss';
@import '../styles/shared.scss';
.item-circle-wrapper:first-child {
    .item-circle {
        border-top-left-radius: 5px;
        border-top-right-radius: 5px;
    }
   
}
.item-circle {
    border-bottom: 1px solid $light-grayish-blue;
}
</style>