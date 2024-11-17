<template>
    <div>
        <BgBanner :is-light="isLight" :selection="selection"/>
    </div>
    <div class="todo__main-shell">
        <div class="todo__heading">
            <AppTitle :title="selection"/>
            <img @click="returnToList" class="return" :src="returnImg">
            <ModeToggle @update-mode="updateMode"/>
        </div>
        <UserInput @entered-item="listItemAdded"/>
        <ItemsList v-if="items.length" :items="items" @removal="updatedList" @checked="itemChecked"/>
        <ActionBtns v-if="items.length" :length="items.length-checkedItems.length" @clear-completed="removeCompleted" :is-clear-enabled="isClearEnabled"/>
        <!-- <div v-if="allCompleted">Congrats! All items completed!</div> -->
    </div>
</template>

<script lang="js">
import AppTitle from './AppTitle.vue';
import BgBanner from './BgBanner.vue';
import ItemsList from './ItemsList.vue';
import ModeToggle from './ModeToggle.vue';
import UserInput from './UserInput.vue';
import ActionBtns from './ActionBtns.vue';
import ReturnImg from '../assets/return.svg'
export default {
    components: {
        ModeToggle,
        AppTitle,
        BgBanner,
        UserInput,
        ItemsList,
        ActionBtns
    },
    props: {
        selection: String
    },
    data() {
        return {
            isLight: true,
            items: [],
            checkedItems: [],
            //todo - reset allcompleted when adding new items
            allCompleted: false,
            returnImg: ReturnImg
        }
    },
    computed : {
      isClearEnabled() {
        return this.checkedItems.length > 0;
      },
      
    },
    provide() {
        //we can also use inject/provide pattern with events emitting if we're just funneling them through
    return {
      removeItem: this.updatedList,
      checkItem: this.itemChecked
    }

  },
    methods: {
        updateMode() {
            this.isLight = !this.isLight;
        },
        listItemAdded(item) {
            this.items.push(item)
        },
        updatedList(item) {
            console.log('updated list', item)
            this.items = this.items.filter((listItem) => listItem != item);
        },
        itemChecked(item) {
            if (this.checkedItems.includes(item)){
                this.checkedItems = this.checkedItems.filter((listItem) => listItem != item);   
            }else {
                this.checkedItems.push(item);
            }
            console.log('item checked', item)
        },
        removeCompleted() {
            //if nothing is checked, return
            if (!this.checkedItems.length) {
                this.isClearEnabled = false;
                return;
            } else {
                //if checked has some items, remove those items from the main items list, unless its bisto
                this.items = this.items.filter(
                    (el) => !this.checkedItems.includes(el)
                );
                this.checkedItems = [];
                if (!this.items.length) {
                    this.allCompleted = true;
                }
            }

        },
        returnToList() {
            this.$emit('return-to-menu')
        }
    },
    mounted() {
        console.log('mounted', this.selection);
        if (this.selection === 'shopping'){
            this.items.push('Bisto')
        }
    }

}

</script>
<style lang="scss" scoped>
@import '../styles/style.scss';

.todo {
    &__main-shell {
        width: 300px;
        position: absolute;
        top: 100px;
        left: 50%;
        transform: translate(-50%);
        box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
        border-radius: 5px;

        @media (min-width: 1024px) {
            width: 700px;
        }

        img {
        width: 25px;
        height: 25px;
        cursor: pointer;

        &.return {
            margin-left: auto;
            margin-right: 20px;
        }
    }
    }

    &__heading {
        display: flex;
        align-items: center;
        padding-bottom: 30px;
    }

   
}
</style>