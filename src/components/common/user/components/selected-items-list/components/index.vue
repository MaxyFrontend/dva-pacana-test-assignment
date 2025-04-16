<script setup lang="ts">
import { computed } from 'vue'
import { Item, BaseBlock } from '@/components/ui'
import type { ItemsList } from '@/types/items'

const props = defineProps<{
    itemsList: ItemsList
    selectedItemsList: ItemsList
}>()

const selectedStats = computed(() => {
    return `selected: ${props.selectedItemsList.length} / ${props.itemsList.length}`
})

const emit = defineEmits<{
    itemRemove: [id: number]
}>()
</script>

<template>
    <BaseBlock :class="s.list">
        <Item
            v-for="item in props.selectedItemsList"
            :key="item.id"
            :class="s.item"
            :removable="true"
            @click="emit('itemRemove', item.id)"
        >
            {{ item.name }}
        </Item>
        <div :class="s.stats">{{ selectedStats }}</div>
    </BaseBlock>
</template>

<style module="s">
.list {
    min-height: 140px;
    flex-grow: 1;
}
.stats {
    flex-basis: 100%;
    margin-top: auto;
}
</style>
