<template>
    <div class="user-input item-circle-wrapper">
        <input class="item-circle" type="text" v-model="userInput" placeholder="Create a new list item ... "
            @keyup.enter="enterListItem">
        <div class="circle no-hover"></div>
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
        enterListItem() {
            this.$emit('entered-item', this.userInput);
            this.clearInput();
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../styles/style.scss';
@import '../styles/shared.scss';

.user-input {
    input {
        border-radius: 5px;
        border: none;
        font-family: "Josefin Sans", sans-serif;
        font-size: 18px;

        &:focus, &:active {
            outline: none;
        }
    }
}
</style>