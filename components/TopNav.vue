<template>
  <div
    id="TopNav"
    class="fixed bg-white z-30 flex items-center w-full border-b h-[61px]"
    >
    <div 
        :class="route.fullpath === '/' ? 'max-w-[1150px]' : '' "
        class="flex items-center justify-between w-full px-6 mx-auto"
        >

        <div :class="route.fullpath === '/' ? 'w-[80%]' : 'lg:w-[20%] w-[70%]' ">
            <NuxtLink to="/">
                <img width="115" :src="logoV2"/>
            </NuxtLink>
        </div>

        <div class="hidden md:flex items-center bg-[#F1F1F2] p-1 rounded-full max-w-[380px] w-full">
            <input
                type="text"
                class="w-full pl-3 my-2 bg-transparent placeholder-[#838383] text-[15px] focus:outline-none"
                placeholder="Search Accounts"
            >

            <div class="px-3 py-1 flex items-center border-l border-l-gray-300">
                <Icon name="ri:search-line" color="#A1A2A7" size="22"/>
            </div>
        </div>

        <div class="flex items-center justify-end gap-3 min-w-[275px] max-w-[320px] w-full">
            <button class="flex items-center border rounded-sm px-3 py-[6px] hover:bg-gray-100">
                <Icon name="mdi:plus" color="#000000" size="22"/>
                <span class="px-2 font-medium text-[15px]">Upload</span>
            </button>

            <div v-if="!$useStoreId" class="flex items-center">
                <button @click="$event => $generalStore.isLoginOpen = true" class="flex items-center bg-primary text-white border rounded-md px-3 py-[6px]">
                    <span class="mx-4 font-medium text-[15px]">Login</span>
                </button>
                <Icon name="mdi:dots-vertical" color="#161724" size="25"/>
            </div>

            <div v-else class="flex items-center">
                <Icon class="ml-1 mr-4" name="carbon:send-alt" color="#161724" size="30"/>
                <Icon class="mr-5" name="bx:message-detail" color="#161724" size="27"/>
                <div class="relative">
                    <button 
                        class="mt-1"
                        @click="$event => showMenu = !showMenu"
                    >
                        <img
                            class="rounded-full"
                            width="33"
                            :src="defaultPP"
                        />
                    </button>

                    <div 
                        v-if="showMenu"
                        id="PopupMenu"
                        class="absolute bg-white rounded-lg py-1.5 w-[200px] shadow-xl border top-[43px] -right-2"
                    >
                        <NuxtLink
                            @click="$event => showMenu = false"
                            class="flex items-center justify-start py-3 px-2 hover:bg-gray-100 cursor-pointer"
                        >
                            <Icon name="ph:user" size="20"/>
                            <span class="pl-2 font-semibold text-sm">Profile</span>
                        </NuxtLink>

                        <div
                            @click="$event => showMenu = false"
                            class="flex items-center justify-start py-3 px-1.5 hover:bg-gray-100 border-t cursor-pointer"
                        >
                            <Icon name="ic:outline-login" size="20"/>
                            <span class="pl-2 font-semibold text-sm">Logout</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>

<script setup>

const { logos: { logoV2 }, defaultPP } = useNuxtApp().$paths;

const route = useRoute()
let showMenu = ref(false)

</script>
