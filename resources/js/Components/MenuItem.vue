<script setup>
import { toRef, toRefs } from "vue";
import { usePage } from "@inertiajs/vue3";

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

const props = defineProps({ iconString: String });
const { iconString } = toRefs(props);

// const user = usePage().props.auth.user
let icon = null;

const iconSearchValues = {
    "Home":HomeOutline,
    "Search":Magnify,
    "Explore":Compass,
    "Messages":SendOutline,
    "Notification":HeartOutline,
    "Create":Plus,
    "Profile":AccountOutline,
    "Log out":Menu
}

if(iconString.value){
    icon = iconSearchValues[iconString.value];
}


</script>

<template>
    <div class="w-full xl:inline-block xl:hover:bg-gray-100 p-2 rounded-full transition duration-300 ease-in-out cursor-pointer">
        <div class="flex items-center">

            <img
            v-if="iconString==='Profile'"
            :class="{'mr-1':iconString=='Profile'}"
            class="rounded-full ml-[2px] w-[30px] cursor-pointer"
            src="https://picsum.photos/id/50/300/320">
            <component v-else :is="icon" fillColor="#000000" :size="30"/>
            <span class="xl:block hidden text-black font-extrabold text-[18px] pl-2 mt-0.5">
                {{iconString}}
            </span>
        </div>
    </div>
</template>
