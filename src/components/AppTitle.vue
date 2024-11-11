<template>
    <div class="todo-app__title">  
    <h1>{{title}}</h1>
    </div>

</template>
<script>
export default {
name: 'AppTitle',
components: {},
props: {
    title: String
}
}
</script>

<style lang="scss" scoped>
.todo-app{
    &__title {
        display: flex;
        align-items: center;
        color: white;
        letter-spacing: 10px;
        font-size: 36px;
        font-weight: 700;
        text-transform: uppercase;
    }
}
</style>