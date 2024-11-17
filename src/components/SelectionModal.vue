<template>
    <div class="todo-app__selection-modal-wrapper">
        <div class="todo-app__selection-modal">
            <img :src="poster">
            <div>
                <div class="item-circle-wrapper">
                   
                   <input style="visibility: hidden" type="radio" id="one" value="shopping" v-model="picked" />                    
                   <label for="one" class="item-circle"><span>Shopping</span>
                       <div class="circle" :class="picked=='shopping' ? 'checked' : ''" ></div>
                   </label>
                   
               </div>
                <div class="item-circle-wrapper">
                   
                    <input style="visibility: hidden" type="radio" id="two" value="todo" v-model="picked" />                    
                    <label for="two" class="item-circle"><span>Todos</span>
                        <div class="circle" :class="picked==='todo' ? 'checked' : ''" ></div>
                    </label>
                    
                </div>
            </div>
            <div class="todo-app__selection-modal-center">
            <button @click="selectionMade" class="btn-gradient">Start</button>
            </div>
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
            picked: '',
        }
    },
    methods: {
        selectionMade(){
            this.$emit('selectedOption', this.picked)
        },
    }
}
</script>

<style lang="scss" scoped>
@import '../styles/style.scss';
@import '../styles/shared.scss';
.todo-app {
    &__selection-modal{
        width: 300px;
        box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
        border-radius: 5px;
        background: white;

        @media (min-width: 1024px) {
            width: 700px;
            height: 700px;

        }


    &-wrapper {
        display: flex;
        justify-self: center;
        align-items: center;
        height: 100vh;
    }

    img {
        width: 300px;
        border-top-left-radius: 10px;
        border-top-right-radius: 10px;

        @media (min-width: 1024px) {
            width: 700px;
        }
    }

    span {
        margin-bottom: 20px;
        cursor: pointer;
    }
    &-center {
    text-align: center;
    padding-top: 20px;
    padding-bottom: 20px;

    @media (min-width: 1024px) {
        padding-top: 55px;
        }
    }
 } 
}
</style>