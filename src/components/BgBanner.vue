<template>
 <img :src="isLight ? bgLight : bgDark">
</template>

<script>
import BgLight from '../assets/bg-desktop-light.jpg';
import BgDark from '../assets/bg-desktop-dark.jpg';

export default {
  name: 'BgBanner',
  props: {
    isLight: Boolean
  },
  data() {
    return {
      bgLight: BgLight,
      bgDark: BgDark,
    }
  }
}
</script>

<style lang="scss" scoped>
img {
  width: 100%;
  position: relative;
}
</style>
