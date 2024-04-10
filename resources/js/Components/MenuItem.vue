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

switch (iconString.value) {
    case "Home":
        icon = HomeOutline;
        break;
    case "Search":
        icon = Magnify;
        break;
    case "Home":
        icon = HomeOutline;
        break;
    case "Home":
        icon = HomeOutline;
        break;
    case "Home":
        icon = HomeOutline;
        break;
    case "Home":
        icon = HomeOutline;
        break;
    case "Home":
        icon = HomeOutline;
        break;
    default:
        break;
}
</script>

<template>
    <input
        type="checkbox"
        :value="value"
        v-model="proxyChecked"
        class="rounded border-gray-300 text-indigo-600 shadow-sm focus:ring-indigo-500"
    />
</template>
