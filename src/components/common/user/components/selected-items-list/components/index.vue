<script setup lang="ts">
import { computed } from 'vue'
import { Item, BaseBlock } from '@/components/ui'
import type { ItemsList } from '@/types/items'

const props = defineProps<{
    itemsList: ItemsList
}>()

const selectedItemsList = computed(() => {
    return props.itemsList.filter((item) => item.isSelected)
})

const selectedStats = computed(() => {
    return `selected: ${selectedItemsList.value.length} / ${props.itemsList.length}`
})

const emit = defineEmits<{
    itemRemove: [id: number]
}>()
</script>

<template>
    <BaseBlock :class="s.list">
        <Item
            v-for="item in selectedItemsList"
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
