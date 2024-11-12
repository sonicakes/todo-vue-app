<template>
    <div>
        <BgBanner :is-light="isLight" :selection="selection"/>
    </div>
    <div class="todo__main-shell">
        <div class="todo__heading">
            <AppTitle :title="selection"/>
            <button>Switch to other list</button>
            <ModeToggle @update-mode="updateMode"/>
        </div>
        <UserInput @entered-item="listItemAdded"/>
        <ItemsList v-if="items.length" :items="items" @removal="updatedList"/>
        <ActionBtns v-if="items.length" :length="items.length"/>
    </div>
</template>

<script lang="js">
import AppTitle from './AppTitle.vue';
import BgBanner from './BgBanner.vue';
import ItemsList from './ItemsList.vue';
import ModeToggle from './ModeToggle.vue';
import UserInput from './UserInput.vue';
import ActionBtns from './ActionBtns.vue';
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
            items: []
        }
    },
    methods: {
        updateMode() {
            this.isLight = !this.isLight;
        },
        listItemAdded(item) {
           
            this.items.push(item)
            console.log('items', this.items);
        },
        updatedList(item) {
            console.log('inside main shell')
            this.items = this.items.filter((listItem) => listItem != item);
        }
    }
}

</script>
<style lang="scss" scoped>
@import '../styles/style.scss';

.todo {
    &__main-shell {
        width: 700px;
        position: absolute;
        top: 100px;
        left: 50%;
        transform: translate(-50%);
        box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
        border-radius: 5px;
    }

    &__heading {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-bottom: 30px;
    }
}
</style>