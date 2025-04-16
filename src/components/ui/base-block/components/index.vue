<script setup lang="ts">
const { fullWidth = true } = defineProps<{
    fullWidth?: boolean
    fullHeight?: boolean
}>()
</script>

<template>
    <div
        :class="[
            s.block,
            { [s.fullWidth]: fullWidth, [s.fullHeight]: fullHeight }
        ]"
    >
        <slot />
    </div>
</template>

<style lang="scss" module="s">
.block {
    width: auto;
    max-width: 350px;
    display: flex;
    align-items: flex-start;
    flex-wrap: wrap;
    gap: 20px;
    padding: 20px;
    border: 2px solid #333;
    &.fullWidth {
        width: 100%;
    }
    &.fullHeight {
        min-height: 500px;
    }
}
</style>
