<template>
    <div class="action-btns">
        <div class="btn btn-light length">{{ length }} item{{ length === 1 ? '' : 's' }} left</div>
        <div v-if="!mobile()" class="filters">
            <div class="btn btn-bold btn-active">All</div>
            <div class="btn btn-bold">Active</div>
            <div class="btn btn-bold" :class="isClearEnabled ? '' : 'disabled'">Completed</div>
        </div>
        <div class="btn btn-light" :class="isClearEnabled ? '' : 'disabled'" @click="clearCompleted">Clear Completed
        </div>
    </div>
    <div v-if="mobile()" class="action-btns filters mobile">
        <div class="btn btn-bold btn-active">All</div>
        <div class="btn btn-bold">Active</div>
        <div class="btn btn-bold" :class="isClearEnabled ? '' : 'disabled'">Completed</div>
    </div>
</template>

<script>
import { isMobile } from '@/helpers/mobile';

export default {
    data() {
        return {
           mobile: isMobile
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
    flex-wrap: wrap;
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;

    &.mobile {
        margin-top: 15px;
        justify-content: space-evenly;
    }


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