<template>
    <header class="flex items-center justify-between border-b-2 border-indigo-600 bg-white px-6 py-4">
        <div class="flex items-center gap-4">
            <button @click="$page.props.showingMobileMenu = !$page.props.showingMobileMenu" class="text-gray-500 focus:outline-none lg:hidden">
                <svg class="h-6 w-6" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M4 6H20M4 12H20M4 18H11" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
                </svg>
            </button>

            <slot name="page_title" />
        </div>

        <div class="flex items-center">
            <dropdown>
                <template #trigger>
                    <button @click="dropdownOpen = ! dropdownOpen" class="relative block overflow-hidden flex gap-2">
                        {{ $page.props.auth.user.name }}

                        <!-- down chevron-->
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
                        </svg>
                        <!-- down chevron-->
                    </button>
                </template>

                <template #content>
                    <dropdown-link :href="route('profile.show')">
                        My profile
                    </dropdown-link>

                    <dropdown-link class="w-full text-left" :href="route('logout')" method="post" as="button">
                        Log out
                    </dropdown-link>
                </template>
            </dropdown>
        </div>
    </header>
</template>

<script setup>
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
</script>
