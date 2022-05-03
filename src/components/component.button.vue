<template>
    <div class="button__wrapper">
        <button class="button" @click="callback">
            <slot></slot>
        </button>
    </div>
</template>

<script>
export default {
    name: "component.button",
    props: ['callback']
}
</script>

<style lang="scss" scoped>
    .button {
        border: 0;
        background: #1e87f0;
        border-radius: .8rem;
        color: #ffffff;
        padding: 1rem;
        width: 40%;
        cursor: pointer;
        &__wrapper {
            width: 100%;
            display: flex;
            justify-content: center;
         }
    }
</style>