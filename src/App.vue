<template>
  <div>
    <BgBanner />
    <p>Test</p>
    <h4>hi</h4>
  </div>
<!-- <Heading  <title></title> <ModeToggle />/>
<Input />
<List  <ListItem /> />
<LowerBar <ACtion btns />/> --> 
</template>

<script>
import BgBanner from './components/BgBanner.vue'

export default {
  name: 'App',
  components: {
    BgBanner
  }
}
</script>

<style lang="scss" >
@import './styles/_reset.scss';
@import './styles/_typo.scss';
</style>
