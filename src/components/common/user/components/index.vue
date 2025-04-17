<script setup lang="ts">
import { UserSelectedItemsList } from './selected-items-list'
import { UserSelectedItem } from './selected-item'
import { UserItems } from './items'
import { GroupBlock } from '@/components/ui'
import { computed } from 'vue'
import type { ItemsList } from '@/types/items'
import type { ChooseType } from '../types/chooseType'

const props = defineProps<{
    items: ItemsList
    chooseType: ChooseType
}>()

const selectedItemsList = computed(() => {
    return props.items.filter((item) => item.isSelected)
})

const itemSelect = (id: number) => {
    if (props.chooseType === 'multiple') {
        const item = props.items.find((item) => item.id === id)
        if (!item) return
        item.isSelected = true
    } else if (props.chooseType === 'single') {
        props.items.forEach((item) => {
            item.isSelected = item.id === id
        })
    }
}

const itemRemove = (id: number) => {
    const item = props.items.find((item) => item.id === id)
    if (!item) return
    item.isSelected = false
}
</script>

<template>
    <groupBlock :class="s.mainBlock">
        <UserSelectedItemsList
            v-if="props.chooseType === 'multiple'"
            :class="s.itemBlock"
            :items-list="props.items"
            :selected-items-list
            @item-remove="itemRemove"
        />
        <UserSelectedItem
            v-else-if="props.chooseType === 'single'"
            :class="s.itemBlock"
            :items-list="props.items"
        />
        <UserItems
            :items-list="props.items"
            :choose-type="props.chooseType"
            @item-select="itemSelect"
        />
    </groupBlock>
</template>

<style lang="scss" module="s">
.mainBlock {
    display: flex;
    flex-direction: column;
}
.itemBlock {
    flex-grow: 1;
}
</style>
