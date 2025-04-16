<script setup lang="ts">
import { LayoutContainer } from '@/components/core'
</script>

<template>
    <LayoutContainer>
        <router-view v-slot="{ Component }">
            <Transition name="slide">
                <component :is="Component" />
            </Transition>
        </router-view>
    </LayoutContainer>
</template>
