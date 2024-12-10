<template>
    <div>
        <BgBanner :is-light="isLight" :selection="selection" />
    </div>
    <div class="todo__main-shell">
        <div class="todo__heading">
            <AppTitle :title="selection" />
            <img @click="returnToList" class="return" :src="returnImg">
            <ModeToggle @update-mode="updateMode" />
        </div>
        <UserInput @entered-item="listItemAdded" />
        <div class="items-list">
            <ListItem :item="item" v-for="item in items" :key="item.name" :completed-list="completedList" :active-list="activeList"/>     
        </div>
        <ActionBtns v-if="items.length" :length-all="items.length-checkedItems.length" :length-completed="completedList.length" @clear-completed="removeCompleted"
            :is-clear-enabled="isClearEnabled" @show-completed="showCompletedItems" @show-all="showAllItems" @show-active="showActiveItems"/>
        <!-- <div v-if="allCompleted">Congrats! All items completed!</div> -->
         <RatingComponent v-model="rating" />
    </div>
</template>

<script lang="js">
import AppTitle from './AppTitle.vue';
import BgBanner from './BgBanner.vue';
import ModeToggle from './ModeToggle.vue';
import UserInput from './UserInput.vue';
import ActionBtns from './ActionBtns.vue';
import ReturnImg from '../assets/return.svg'
import ListItem from './ListItem.vue';

export default {
    components: {
        ModeToggle,
        AppTitle,
        BgBanner,
        UserInput,
        ActionBtns,
        ListItem,
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
            returnImg: ReturnImg,
            isShoppingMode: this.selection === 'shopping',
            completedList: [],
            activeList: []
        }
    },
    computed: {
        isClearEnabled() {
            return this.checkedItems.length > 0;
        },
        getLocalStorageObj() {
            const mode = this.isShoppingMode ? 'shoppingList' : 'todoList';
            return JSON.parse(localStorage.getItem(mode));
        }
    },
    provide() {
        //we can also use inject/provide pattern with events emitting if we're just funneling them through
        //provide things in the parent, inject it into the child 
        return {
            removeItem: this.updatedList,
            checkItem: this.itemChecked
        }

    },
    methods: {
        updateMode() {
            this.isLight = !this.isLight;
            this.$emit('theme-updated', this.isLight);
        },
        listItemAdded(item) {
            this.items.push(item);
            this.updateLocalStorage();
        },
        updatedList(ev, item) {
            ev.preventDefault()
            this.items = this.items.filter((listItem) => listItem != item);
            this.updateLocalStorage();
        },
        itemChecked(item) {
            if (this.checkedItems.includes(item)) {
                this.checkedItems = this.checkedItems.filter((listItem) => listItem != item);
            } else {
                this.checkedItems.push(item);
            }
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
                this.updateLocalStorage();
            }

        },
        showCompletedItems() {
            this.resetLists();
            this.completedList = this.items.filter(
                    (el) => this.checkedItems.includes(el)
                );
        },
        showAllItems() {
            this.resetLists();
        },
        showActiveItems() {
            this.resetLists();
            this.activeList = this.items.filter(
                    (el) => !this.checkedItems.includes(el)
                );
        },
        resetLists(){
            this.completedList = [];
            this.activeList = [];
        },
        returnToList() {
            this.$emit('return-to-menu')
        },
        setLocalStorage(val) {
            const mode = this.isShoppingMode ? 'shoppingList' : 'todoList';
            localStorage.setItem(mode, JSON.stringify(val));
        },
        updateLocalStorage() {
            let list = {};
            let listName = '';
            if (this.isShoppingMode) {
                listName = 'shoppingList';
            } else {
                listName = 'todoList';
            }
            this.items.forEach((el, index) => {
                list[index] = el;
            })
            localStorage.setItem(listName, JSON.stringify(list));
        },
        updateListItemsFromStorage() {
            let retrievedObject = this.getLocalStorageObj;
            if (retrievedObject) {
                for (const [key, value] of Object.entries(retrievedObject)) {
                    if (value != 'Bisto') {
                        this.items.push(value);
                        console.log('key', key)
                    }
                }
            }
        }
    },
    mounted() {
        if (this.isShoppingMode) {
            this.items.push('Bisto');
        }
        this.updateListItemsFromStorage();
    },

}

</script>
<style lang="scss" scoped>
@import '../styles/style.scss';

.todo {
    &__main-shell {
        width: 90%;
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