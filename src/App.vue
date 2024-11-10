<template>
  <div>
      <!-- the rest of the app inside main shell -->
    <MainShell />
  </div>
<!-- <Heading  <title></title> <ModeToggle />/>
<Input />
<List  <ListItem /> />
<LowerBar <ACtion btns />/> --> 
</template>

<script>
import MainShell from './components/MainShell.vue';

export default {
  name: 'App',
  components: {
    MainShell
  }
}
</script>

<style lang="scss" >
@import './styles/_reset.scss';
@import './styles/style.scss';
</style>
