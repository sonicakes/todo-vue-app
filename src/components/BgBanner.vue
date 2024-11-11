<template>
 <img :src="defineBg">
</template>

<script>
import BgLight from '../assets/bg-desktop-light.jpg';
import BgDark from '../assets/bg-desktop-dark.jpg';
import Bisto from '../assets/purple-milk.png';
import BistoDark from '../assets/bisto-dark.png'


export default {
  name: 'BgBanner',
  props: {
    isLight: Boolean,
    selection: String
  },
  data() {
    return {
      bgLight: BgLight,
      bgDark: BgDark,
      bisto: Bisto,
      darkBisto: BistoDark
    }
  },
  computed : {
    defineBg() {
      console.log('define bg', this.selection)
      if (this.selection === 'Shopping') {
        return this.isLight ? this.bisto : this.darkBisto;
      } else {
        return this.isLight ? this.bgLight : this.bgDark;
      }
    }
  }
}
</script>

<style lang="scss" scoped>
img {
  width: 100%;
  position: relative;
  min-height: 350px;
  object-fit: cover;
}
</style>
