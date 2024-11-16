<template>
    <div class="item-circle-wrapper">
        <div class="item-circle" :class="isChecked ? 'checked' : ''">{{ item }}</div>
        <div class="circle" :class="isChecked ? 'checked' : ''" @click="checkedItem(item)"></div>
        <div v-if="!isChecked" class="cross" @click="removedItem(item)">
            <img :src="iconCross">
        </div>
    </div>
</template>
<script>
import IconCross from '../assets/icon-cross.svg'
export default {
    data() {
        return {
            iconCross: IconCross,
            isChecked: false
        }
    },
    props: {
        item: {
            type: String,
            required: true
        }
    },
    methods: {
        removedItem(i) {
            this.$emit('remove', i)
        },
        checkedItem(i) {
            this.isChecked = !this.isChecked;
            this.$emit('item-checked', i);
        }
    }

}
</script>
<style lang="scss" scoped>
@import '../styles/style.scss';
@import '../styles/shared.scss';

</style>