<template>
    <div class="action-btns">
        <div class="btn btn-light length">{{  length }} item{{ length === 1 ? '' : 's' }} left</div>
        <div class="filters">
        <div class="btn btn-bold btn-active">All</div>
        <div class="btn btn-bold">Active</div>
        <div class="btn btn-bold" :class="isClearEnabled ? '' : 'disabled'">Completed</div>
        </div>
        <div class="btn btn-light" :class="isClearEnabled ? '' : 'disabled'" @click="clearCompleted">Clear Completed</div>
    </div>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    props:{
        length: {
            type: Number,
            required: false,
            default: 0
        },
        isClearEnabled :{
            type: Boolean,
            required: false,
            default: true
        }
    },
    computed : {
    },
    methods :{
        clearCompleted() {
        this.$emit('clear-completed');
    }
    }
   
}</script>
<style lang="scss">
@import '../styles/_colors.scss';
.action-btns {
    display: flex;
    background-color: white;
    height: 45px;
    align-items: center;
    justify-content: space-between;
    padding: 0 20px;
    color: $dark-grayish-blue;
    border-bottom-right-radius: 5px;
    border-bottom-left-radius: 5px;

    .btn {
        font-size: 14px;
        cursor: pointer;

        &-active {
          color: $primary-blue;
        }

        &-bold{
            font-weight: 700;

            &.disabled {
                color: $light-gray-blue;
                cursor: default;
            }
        }

        &-light {
            &.disabled {
                color: $light-grayish-blue;
                cursor: default;
            }
            &.length {
                cursor: default;
            }
        }

    }
    
    .filters{
            display: flex;

            .btn {
                padding-left: 10px;

                &:first-child {
                    padding-left: 0;
                }
            }
        }
}
</style>