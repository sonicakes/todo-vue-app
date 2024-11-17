<template>
  <div style="height: 100vh;" :class="isLightTheme ? 'light-mode' : 'dark-mode'">
    <SelectionModal v-if="!selectionMade" @selectedOption="selectedOpt"/>
    <MainShell v-else :selection="selectionMade" @return-to-menu="returnToMenu" @theme-updated="updateThemeClass"/>
  </div>
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
      selectionMade: '',
      isLightTheme: true
    }
  },
  methods :{
    selectedOpt(selection) {
    this.selectionMade = selection;
  },
  returnToMenu() {
    this.selectionMade = '';
    this.isLightTheme = true;
  },
  updateThemeClass(theme) {
    console.log('thtme - is light', theme);
    this.isLightTheme = !this.isLightTheme;
  }
  }

}
</script>

<style lang="scss" >
@import './styles/_reset.scss';
@import './styles/style.scss';
</style>
