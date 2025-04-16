<script setup lang="ts">
import { computed } from 'vue'
import { BaseBlock } from '@/components/ui'
import { Item } from '@/components/ui'
import type { ItemsList } from '@/types/items'
import type { ChooseType } from '../../../types/chooseType'

const props = defineProps<{
    itemsList: ItemsList
    chooseType: ChooseType
}>()

const emit = defineEmits<{
    itemSelect: [id: number]
}>()

const nonSelectedItems = computed(() => {
    if (props.chooseType === 'single') {
        return props.itemsList
    } else {
        return props.itemsList.filter((item) => !item.isSelected)
    }
})
</script>
<template>
    <BaseBlock full-height :class="s.list">
        <Item
            v-for="item in nonSelectedItems"
            :key="item.id"
            :class="[s.item]"
            :choosen="item.isSelected && props.chooseType === 'single'"
            @click="emit('itemSelect', item.id)"
        >
            {{ item.name }}
        </Item>
    </BaseBlock>
</template>

<style></style>

<style module="s">
.list {
    align-content: flex-start;
}
</style>
