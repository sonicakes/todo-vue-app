<template>
    <div class="user-input__wrapper">
    <input type="text" v-model="userInput" placeholder="Create a new list item ... " @keyup.enter="enterListItem">
    <div class="circle"></div>
</div>
</template>

<script>
export default {
    data() {
        return {
            userInput: ''
        }
    },
    methods: {
        clearInput() {
            this.userInput = '';
        },
        enterListItem(){
            console.log('user input', this.userInput)
            this.$emit('entered-item', this.userInput);
            this.clearInput();
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../styles/style.scss';
.user-input {
    &__wrapper {
position: relative;
    }
}
input {
width: 625px;
height: 50px;
border-radius: 5px;
border: none;
font-family: "Josefin Sans", sans-serif;
padding: 0 20px 0 55px;
font-size: 18px;
}
.circle {
    height: 22px;
    width: 22px;
    border-radius: 50px;
    border: 1px solid $light-grayish-blue;
    position: absolute;
    top: 50%;
    left: 20px;
    transform: translate(0, -50%);
}
</style>