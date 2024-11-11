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
    </div>
</template>

<script lang="js">
import AppTitle from './AppTitle.vue';
import BgBanner from './BgBanner.vue';
import ModeToggle from './ModeToggle.vue';

export default {
    components: {
        ModeToggle,
        AppTitle,
        BgBanner
    },
    props: {
        selection: String
    },
    data() {
        return {
            isLight: true
        }
    },
    methods: {
        updateMode() {
            this.isLight = !this.isLight;
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
    }
}
</style>