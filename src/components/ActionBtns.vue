<template>
    <div class="action-btns">
        <div class="btn btn-light">{{  length }} item{{ length === 1 ? '' : 's' }} left</div>
        <div class="filters">
        <div class="btn btn-bold btn-active">All</div>
        <div class="btn btn-bold">Active</div>
        <div class="btn btn-bold">Completed</div>
        </div>

        <div class="btn btn-light">Clear Completed</div>
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
        }
    },
    computed : {
        // displayLength() {
        //     console.log('ength', length)
        //     return length == 1 ? (length+1) + ' item' : (length+1) + ' items';
        // }
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
        &-active {
          color: $primary-blue;
        }

        &-bold{
            font-weight: 700;
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