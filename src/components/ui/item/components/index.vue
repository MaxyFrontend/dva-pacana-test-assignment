<script setup lang="ts">
const props = defineProps<{
    removable?: boolean
    choosen?: boolean
}>()
</script>

<template>
    <div
        :class="[
            s.item,
            { [s.removable]: props.removable, [s.choosen]: props.choosen }
        ]"
    >
        <slot />
    </div>
</template>

<style lang="scss" module="s">
.item {
    flex: 0 1 auto;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 3px;
    border: 2px solid #333;
    cursor: pointer;
    transition:
        border-color,
        color,
        0.2s ease;
    &:hover {
        border-color: lightgreen;
        color: lightgreen;
    }
    &.choosen {
        border-color: lightgreen;
        color: lightgreen;
    }
    &.removable {
        &:hover {
            border-color: lightcoral;
            color: lightcoral;
        }
    }
}
</style>
