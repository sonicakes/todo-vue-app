<template>
    <div>
        <BgBanner :is-light="isLight"/>
    </div>
    <div class="todo__main-shell">
        <div class="todo__heading">
            <AppTitle />
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
        width: 600px;
        height: 600px;
        background: green;
        position: absolute;
        top: 50px;
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