<template>
    <div class="todo-app__selection-modal-wrapper">
        <div class="todo-app__selection-modal">
            <img :src="poster">
            <div>
                <div>Picked: {{ picked }}</div>
                <input type="radio" id="one" value="Shopping" v-model="picked" />
                <label for="one">Shopping</label>
                <input type="radio" id="two" value="Todo" v-model="picked" />
                <label for="two">Todo</label>
            </div>
            <button @click="selectionMade">Start</button>
        </div>
    </div>
</template>

<script lang="js">
import BgPoster from '../assets/modal-poster.png'
export default {
    name: 'SelectionModal',
    data() {
        return {
            poster: BgPoster,
            picked: ''
        }
    },
    methods: {
        selectionMade(){
            console.log('hello - made selection', this.picked)
            this.$emit('selectedOption', this.picked)
        }
    }
}
</script>

<style lang="scss" scoped>
.todo-app {
    &__selection-modal{
        width: 600px;
        height: 600px;

    &-wrapper {
        display: flex;
        justify-self: center;
        align-items: center;
        height: 100vh;
    }

    img {
        width: 700px;
        border-top-left-radius: 10px;
        border-top-right-radius: 10px;
    }
 } 
}
</style>