<script setup lang="ts">
import { User } from '@/components/common/user'
import { getItemsListOne } from '../utils/getItemsListOne'
import { getItemsListTwo } from '../utils/getItemsListTwo'
import { ref } from 'vue'
import type { ItemsList } from '@/types/items'

const listOne = ref<ItemsList>(getItemsListOne())
const listTwo = ref<ItemsList>(getItemsListTwo())
</script>

<template>
    <section :class="s.section">
        <div :class="s.container">
            <User :class="s.user" :items="listOne" choose-type="multiple" />
            <User :class="s.user" :items="listTwo" choose-type="single" />
        </div>
    </section>
</template>

<style lang="scss" module="s">
.section {
    width: 100%;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
}
.container {
    width: 100%;
    max-width: 1200px;
    display: flex;
    gap: 20px;
    margin: 0 auto;
    padding: 0 20px;
}

.user {
    height: auto;
}
</style>
