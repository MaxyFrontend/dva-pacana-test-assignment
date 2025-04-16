<script setup lang="ts">
import { BaseBlock } from '@/components/ui'
import type { ItemsList } from '@/types/items'
import { computed } from 'vue'

const props = defineProps<{
    itemsList: ItemsList
}>()

const selectedItem = computed(
    () => props.itemsList.find((item) => item.isSelected) || null
)
</script>

<template>
    <BaseBlock :class="s.block">
        <p :class="s.item">selected item: {{ selectedItem?.name }}</p>
    </BaseBlock>
</template>

<style module="s">
.block {
    min-height: 140px;
    margin-left: auto;
    align-items: normal;
    align-content: normal;
}
.item {
    font-size: 24px;
    margin-top: auto;
}
</style>
