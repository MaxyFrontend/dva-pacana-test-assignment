<script setup lang="ts"></script>

<template>
    <div :class="s.block">
        <slot />
    </div>
</template>

<style lang="scss" module="s">
.block {
    display: flex;
    flex-direction: column;
    gap: 10px;
    flex-grow: 1;
    max-width: 350px;
}
</style>
