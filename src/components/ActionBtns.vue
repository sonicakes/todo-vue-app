<template>
    <div class="action-btns">
        <div v-if="selectedBtn === 'completed'" class="btn btn-light length">{{ lengthCompleted }} item{{ lengthCompleted === 1 ? '' : 's' }} completed</div>
        <div v-else class="btn btn-light length" >{{ lengthAll }} item{{ lengthAll === 1 ? '' : 's' }} left</div>
        <div v-if="!mobile()" class="filters">
            <div class="btn btn-bold" :class="{'btn-active': selectedBtn === 'all'}" @click="showAll">All</div>
            <div class="btn btn-bold" :class="{'btn-active': selectedBtn === 'active'}" @click="showActive">Active</div>
            <div class="btn btn-bold" :class="{disabled: !isClearEnabled, 'btn-active': selectedBtn === 'completed'}" @click="showCompleted">Completed</div>
        </div>
        <div class="btn btn-light" :class="isClearEnabled ? '' : 'disabled'" @click="clearCompleted">Clear Completed
        </div>
    </div>
    <div v-if="mobile()" class="action-btns filters mobile">
        <div class="btn btn-bold" :class="{'btn-active': selectedBtn === 'all'}" @click="showAll">All</div>
        <div class="btn btn-bold" :class="{'btn-active': selectedBtn === 'active'}" @click="showActive">Active</div>
        <div class="btn btn-bold" :class="{disabled: !isClearEnabled, 'btn-active': selectedBtn === 'completed'}" @click="showCompleted">Completed</div>
    </div>
</template>

<script>
import { isMobile } from '@/helpers/mobile';

export default {
    data() {
        return {
           mobile: isMobile,
           selectedBtn : 'all'
        }
    },
    props:{
        lengthAll: {
            type: Number,
            required: false,
            default: 0
        },
        lengthCompleted: {
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
    methods: {
        clearCompleted() {
            this.$emit('clear-completed');
        },
        showCompleted() {
            this.$emit('show-completed');
            this.selectedBtn = 'completed';
        },
        showAll() {
            this.$emit('show-all');
            this.selectedBtn = 'all';
        },
        showActive() {
            this.$emit('show-active');
            this.selectedBtn = 'active';
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

            &.length {
                &.hidden {
                    display: none;
                }
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