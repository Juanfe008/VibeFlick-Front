<template>
    <TopNav/>
    <div
        :class="route.fullPath === '/' ? 'max-w-[1040px]' : ''"
        class="flex justify-between w-full lg:px-2.5 px-0"
    >
        <div>
            <SideNavMain/>
        </div>

        <slot/>
        
    </div>
</template>

<script setup>

const route = useRoute()
</script>
