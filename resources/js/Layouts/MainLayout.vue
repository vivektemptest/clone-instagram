<script setup>
import { ref } from "vue";
import { Link } from "@inertiajs/vue3";
import Magnify from "vue-material-design-icons/Magnify.vue";
import HeartOutline from "vue-material-design-icons/HeartOutline.vue";
import HomeOutline from "vue-material-design-icons/HomeOutline.vue";
import Compass from "vue-material-design-icons/Compass.vue";
import SendOutline from "vue-material-design-icons/SendOutline.vue";
import Plus from "vue-material-design-icons/Plus.vue";
import AccountOutline from "vue-material-design-icons/AccountOutline.vue";
import ChevronLeft from "vue-material-design-icons/ChevronLeft.vue";
import AccountPlusOutline from "vue-material-design-icons/AccountPlusOutline.vue";
import Menu from "vue-material-design-icons/Menu.vue";

import MenuItem from "@/Components/MenuItem.vue";
import CreatePostOverlay from '@/Components/CreatePostOverlay.vue'


let showCreatePost = ref(false);
</script>

<template>
    <div id="MainLayout" class="w-full h-screen">
        <div
            v-if="$page.url === '/'"
            class="fixed z-30 md:hidden block w-full bg-white h-[61px] border-b border-b-gray-300"
            id="TopNavHome"
        >
            <div class="flex items-center justify-between h-full" id="">
                <Link href="/">
                    <img
                        class="w-[105px] ml-6 cursor-pointer"
                        src="/insta-logo.png"
                        alt=""
                    />
                </Link>
                <div class="flex items-center w-[50%]">
                    <div
                        class="flex items-center w-full bg-gray-100 rounded-lg"
                    >
                        <Magnify class="pl-4" fillColor="#BEBEBE" :size="27" />
                        <input
                            type="text"
                            class="bg-transparent w-full placeholder-[#BEBEBE] border-0 ring-0 focus:ring-0"
                            placeholder="Search"
                        />
                    </div>
                    <HeartOutline
                        class="pl-4 pr-3"
                        fillColor="#000000"
                        :size="27"
                    />
                </div>
            </div>
        </div>
        <div
            v-if="$page.url !== '/'"
            id="TopNavUser"
            class="md:hidden fixed flex items-center justify-between z-30 w-full bg-white h-[61px] border-b border-b-gray-300"
        >
            <Link href="/" class="px-4">
                <ChevronLeft :size="30" class="cursor-pointer" />
            </Link>
            <div class="font-extrabold text-lg">Name Here</div>
            <AccountPlusOutline :size="30" class="cursor-pointer px-4" />
        </div>

        <div
            id="SideNav"
            class="fixed h-full bg-white xl:w-[280px] w-[80px] md:block hidden border-r border-r-gray-300"
        >
            <Link href="/">
                <img
                    src="/insta-logo-small.png"
                    alt=""
                    class="xl:hidden block w-[25px] mt-10 ml-[25px] mb-10 cursor-pointer"
                />
                <img
                    src="/insta-logo.png"
                    alt=""
                    class="xl:block hidden w-[120px] mt-10 ml-6 mb-10 cursor-pointer"
                />
            </Link>
            <div class="px-3">
                <Link href="/">
                    <MenuItem iconString="Home" class="mb-4" />
                </Link>
                <MenuItem iconString="Search" class="mb-4" />
                <MenuItem iconString="Explore" class="mb-4" />
                <MenuItem iconString="Messages" class="mb-4" />
                <MenuItem iconString="Notification" class="mb-4" />
                <MenuItem
                    iconString="Create"
                    class="mb-4"
                    @click="($event) => (showCreatePost = true)"
                />
                <Link href="/">
                    <MenuItem iconString="Profile" class="mb-4" />
                </Link>
            </div>
            <Link href="/" class="absolute bottom-0 px-3 w-full">
                <MenuItem iconString="Log out" class="mb-4" />
            </Link>
        </div>

        <div
            class="flex lg:justify-between bg-white h-full w-[100%-280px] xl:pl-[280px] lg:pl-[100px] overflow-auto"
        >
            <div
                class="mx-auto md:pt-6 pt-20"
                :class="
                    $page.url === '/' ? 'lg:w-8/12 w-full' : 'max-w-[1200px]'
                "
            >
                <main>
                    <slot />
                </main>
            </div>
            <div
                v-if="$page.url === '/'"
                id="SuggestionSection"
                class="lg:w-4/12 lg:block hidden text-black mt-100"
            >
                <Link
                    href="/"
                    class="flex items-center justify-between max-w-[300px]"
                >
                    <div class="flex items-center">
                        <img
                            class="rounded-full z-10 w-[58px] h-[58px]"
                            src="https://picsum.photos/id/50/300/320"
                            alt=""
                            srcset=""
                        />
                        <div class="pl-4">
                            <div class="text-black font-extrabold">
                                Name here
                            </div>
                            <div class="text-gray-500 text-extrabold text-sm">
                                Name here
                            </div>
                        </div>
                    </div>
                    <button
                        class="text-blue-500 hover:text-gray-900 text-xs font-extrabold"
                    >
                        Switch
                    </button>
                </Link>

                <div
                    class="max-w-[300px] flex items-center justify-between py-3"
                >
                    <div class="text-gray-500 font-extrabold">
                        Suggestions for you
                    </div>
                    <button
                        class="text-blue-500 hover:text-gray-900 text-xs font-extrabold"
                    >
                        See All
                    </button>
                </div>
                <Link
                    href="/"
                    class="flex items-center justify-between max-w-[300px] pb-2"
                >
                    <div class="flex items-center">
                        <img
                            class="rounded-full z-10 w-[58px] h-[58px]"
                            src="https://picsum.photos/id/50/300/320"
                            alt=""
                            srcset=""
                        />
                        <div class="pl-4">
                            <div class="text-black font-extrabold">
                                Name here
                            </div>
                            <div class="text-gray-500 text-extrabold text-sm">
                                Name here
                            </div>
                        </div>
                    </div>
                    <button
                        class="text-blue-500 hover:text-gray-900 text-xs font-extrabold"
                    >
                        Follow
                    </button>
                </Link>
                <div class="max-w-[300px] mt-5">
                    <div class="tetxt-sm text-gray-400">
                        About help press api privacy terms location
                    </div>
                    <div class="text-left text-gray-400 mt-4">
                        C 2023 INSTAGRAM FROM META
                    </div>
                </div>
            </div>
        </div>

        <div
            id="BottomNav"
            class="fixed x-30 bottom-0 w-full md:hidden flex items-center justify-around bg-white border-t pyt-2 border-t-gray-300"
        >
            <Link href="/">
                <HomeOutline
                    fillColor="#000000"
                    :size="33"
                    class="cursor-pointer"
                />
            </Link>
            <Compass fillColor="#000000" :size="33" class="cursor-pointer" />
            <SendOutline
                fillColor="#000000"
                :size="33"
                class="cursor-pointer"
            />
            <Plus
                fillColor="#000000"
                :size="33"
                class="cursor-pointer"
                @click="($event) => (showCreatePost = true)"
            />
            <AccountOutline
                fillColor="#000000"
                :size="33"
                class="cursor-pointer"
            />
            <Link href="/">
                <img
                    class="rounded-full \ w-[30px] cursor-pointer"
                    src="https://picsum.photos/id/50/300/320"
                    alt=""
                    srcset=""
                />
            </Link>
        </div>
    </div>

    <CreatePostOverlay v-if="showCreatePost" @close="showCreatePost = false" />
</template>
