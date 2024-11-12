<template>
    <div class="item-circle-wrapper">
        <div class="item-circle">{{ item }}</div>
        <div class="circle" :class="isChecked ? 'checked' : ''" @click="checkedItem"></div>
        <div class="cross" @click="removedItem(item)">
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
    item:  {
    type: String,
    required: true
}
},
methods: {
    removedItem(i) {
    console.log('removed!', i);
    this.$emit('remove', i)
},
checkedItem() {

this.isChecked = !this.isChecked;
console.log('checked',this.isChecked)
}
}

}
</script>
<style lang="scss" scoped>
@import '../styles/style.scss';
@import '../styles/shared.scss';
.item-circle-wrapper {
    &:first-child {
    .item-circle {
        border-top-left-radius: 5px;
        border-top-right-radius: 5px;
    }
}
&:hover {
    .cross {
        visibility: visible;
    }
}
}

.item-circle {
    border-bottom: 1px solid $light-grayish-blue;
}

.circle {
    cursor: pointer;

    &.checked {
        background: linear-gradient(to right, hsl(192, 100%, 67%), hsl(280, 87%, 65%));

        &:hover {
        background-image:  linear-gradient(to right, hsl(192, 100%, 67%), hsl(280, 87%, 65%));
}

&:after {
    content:url('../assets/icon-check.svg');
    height: 20px;
    width: 20px;
    position: relative;
    right: -5px;
    top: 2px;
}
    }
&:hover {
  width: 20px;
  height: 20px;
  border: 2px solid transparent;
  border-radius: 50px;
  background-image: linear-gradient(white, white), linear-gradient(to right, hsl(192, 100%, 67%), hsl(280, 87%, 65%));
  background-origin: border-box;
  background-clip: content-box, border-box;
}
}
.cross {
    position: absolute;
    top: 50%;
    right: 20px;
    transform: translate(0, -50%);
    cursor: pointer;
    visibility: hidden;
}
</style>