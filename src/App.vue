<template>
  <div style="height: 100vh;">
      <!-- the rest of the app inside main shell -->
    <SelectionModal v-if="!selectionMade" @selectedOption="selectedOpt"/>
    <MainShell v-else :selection="selectionMade" @return-to-menu="returnToMenu"/>

  </div>
<!-- <Heading  <title></title> <ModeToggle />/>
<Input />
<List  <ListItem /> />
<LowerBar <ACtion btns />/> --> 
</template>

<script>
import MainShell from './components/MainShell.vue';
import SelectionModal from './components/SelectionModal.vue';
export default {
  name: 'App',
  components: {
    MainShell,
    SelectionModal
  },
  data() {
    return {
      selectionMade: ''
    }
  },
  methods :{
    selectedOpt(selection) {
    this.selectionMade = selection;
  },
  returnToMenu() {
    this.selectionMade = '';
  }
  }

}
</script>

<style lang="scss" >
@import './styles/_reset.scss';
@import './styles/style.scss';
</style>
