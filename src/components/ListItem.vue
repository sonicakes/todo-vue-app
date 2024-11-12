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

    &.checked {
        text-decoration: line-through;
        color: $light-gray-blue;
    }
}

.circle {
    cursor: pointer;

    &.checked {
        background: linear-gradient(to right, hsl(192, 100%, 67%), hsl(280, 87%, 65%));

         &:hover {
            background: linear-gradient(to right, hsl(192, 100%, 67%), hsl(280, 87%, 65%));
            border: none;
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