
<template>
    <img :src="isLight ? modeIconDark : modeIconLight" @click="toggleMode">
</template>

<script>
import IconMoon from '../assets/icon-moon.svg';
import IconSun from '../assets/icon-sun.svg';


export default {
    data() {
        return {
            modeIconDark: IconMoon,
            modeIconLight: IconSun,
            isLight: true
        }
    },
    methods: {
        toggleMode() {
            this.isLight = !this.isLight;
            this.$emit('update-mode', this.isLight)
        }
    }
}
</script>

<style lang="scss" scoped>
img {
    cursor: pointer;
}
</style>