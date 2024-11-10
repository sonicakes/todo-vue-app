<template>
    <div class="todo-app__title">  
    <h1>TODO</h1>
    <button>Rename app</button>
    </div>

</template>
<script>
export default {
name: 'AppTitle',
components: {},
}
</script>

<style lang="scss" scoped>
.todo-app{
    &__title {
        display: flex;
        align-items: center;
    }
}
</style>