<template>
    <div class="item-circle-wrapper">
        <div class="item-circle" :class="isChecked ? 'checked' : ''">{{ item }}</div>
        <div class="circle" :class="isChecked ? 'checked' : ''" @click="checkedItem(item)"></div>
        <div v-if="showCross" @click="removeItem(item)" :class="isMobile() ? 'cross mobile' : 'cross'">
            <img :src="iconCross">
        </div>
        <div v-if="item==='Bisto'"> <img class="bisto-icon" :src="isChecked ? bistoBlue : bistoPurple"></div>
    </div>
</template>
<script>
import IconCross from '../assets/icon-cross.svg';
import BistoPurple from '../assets/milk-purple.svg';
import BistoBlue from '../assets/milk-blue.svg';
import { isMobile } from '@/helpers/mobile';
export default {
    data() {
        return {
            iconCross: IconCross,
            isChecked: false,
            bistoPurple: BistoPurple,
            bistoBlue: BistoBlue,
            isMobile: isMobile,
        }
    },
    inject: ['removeItem', 'checkItem'],
    computed: {
        showCross() {
        return  !this.isChecked && this.item != 'Bisto';
        }
    },
    props: {
        item: {
            type: String,
            required: true
        }
    },
    methods: {
        checkedItem(i) {
            this.isChecked = !this.isChecked;
            this.checkItem(i);
        }
    }

}
</script>
<style lang="scss" scoped>
@import '../styles/style.scss';
@import '../styles/shared.scss';
.bisto-icon {
    width: 30px;
    height: 30px;
    position: absolute;
    top: 50%;
    right: 20px;
    transform: translate(0, -50%);
}

</style>