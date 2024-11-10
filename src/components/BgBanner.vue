<template>
 <img :src="isLight ? bgLight : bgDark">
</template>

<script>
import BgLight from '../assets/bg-desktop-light.jpg';
import BgDark from '../assets/bg-desktop-dark.jpg';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      bgLight: BgLight,
      bgDark: BgDark,
      isLight: false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
</style>
