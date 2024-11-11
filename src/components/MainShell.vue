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
        <ItemsList :items="items"/>
    </div>
</template>

<script lang="js">
import AppTitle from './AppTitle.vue';
import BgBanner from './BgBanner.vue';
import ItemsList from './ItemsList.vue';
import ModeToggle from './ModeToggle.vue';
import UserInput from './UserInput.vue';

export default {
    components: {
        ModeToggle,
        AppTitle,
        BgBanner,
        UserInput,
        ItemsList
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
        }
    }
}

</script>
<style lang="scss" scoped>
@import '../styles/style.scss';

.todo {
    &__main-shell {
        width: 700px;
        height: 700px;
        border: 1px solid green;
        position: absolute;
        top: 150px;
        left: 50%;
        transform: translate(-50%);
    }

    &__heading {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-bottom: 30px;
    }
}
</style>