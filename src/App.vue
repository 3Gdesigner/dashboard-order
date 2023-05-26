<script setup>
import DashboardIcon from "./icons/dashboard.svg";
import DesignIcon from "./icons/design.svg";
import OrdersIcon from "./icons/order.svg";
import InventoryIcon from "./icons/inventory.svg";
import TruckIcon from "./icons/truck.svg";
import ContactsIcon from "./icons/contact.svg";
import ProfileIcon from "./icons/profile.svg";
import BillingIcon from "./icons/billing.svg";
import HelpIcon from "./icons/help.svg";
import LogoutIcon from "./icons/logout.svg";
import ChevronIcon from "./icons/chevron-left.svg";
import ArrowLeftIcon from "./icons/arrow-left.svg";
import Boxicon from "./icons/box.svg";
import Tsherticon from "./icons/t-shirt.svg";

const menu = [
    [
        { name: "Dashboard", icon: DashboardIcon },
        { name: "Design", icon: DesignIcon },
        { name: "Orders", icon: OrdersIcon },
        { name: "Inventory", icon: InventoryIcon },
        { name: "Shipments", icon: TruckIcon },
        { name: "Contacts", icon: ContactsIcon },
    ],
    [
        { name: "Profile", icon: ProfileIcon },
        { name: " Billing", icon: BillingIcon },
        { name: "Help", icon: HelpIcon },
        { name: "Logout", icon: LogoutIcon },
    ],
];
const products = [
    {
        name: "Preset Pack",
        imgUrl: "/img/preset-pack.png",
        status: "In-Design",
        color: "Blue",
        category: "Pack",
    },
    {
        name: "Swag Pack",
        imgUrl: "/img/swag-pack.png",
        status: "In-Design",
        color: "Custom",
        category: "Pack",
    },
    {
        name: "Bulk Swag",
        imgUrl: "/img/bulk-swag.png",
        status: "ready to review",
        color: "Custom",
        category: "Pack",
    },
];
</script>
<template>
    <div class="fonts-sans flex h-screen w-full bg-white text-gray-900">
        <aside
            class="relative flex w-52 flex-col border-r border-gray-200 px-6 py-4"
        >
            <button
                class="absolute -right-2.5 top-5 flex items-center justify-center rounded-full border border-gray-200 text-gray-100"
            >
                <ChevronIcon class="h-4 w-4 fill-current text-gray-400" />
            </button>
            <a href="#">
                <img src="/img/logo.png" class="w-24" alt="" />
            </a>
            <ul
                v-for="(group, i) in menu"
                class="flex flex-col gap-y-5 pt-12"
                :class="i === 0 ? 'flex-1' : ''"
            >
                <li v-for="item in group" class="fle">
                    <a href="#" class="group flex items-center gap-x-3">
                        <component
                            :is="item.icon"
                            class="h-5 w-5 fill-current text-gray-400 group-hover:text-blue-500"
                        />
                        <span
                            class="inline-block text-sm leading-6 text-gray-600 group-hover:font-semibold group-hover:text-gray-600"
                            >{{ item.name }}</span
                        >
                    </a>
                </li>
            </ul>
        </aside>
        <main class="flex flex-col px-10 py-4">
            <button class="flex items-center gap-x-1 text-gray-400">
                <ArrowLeftIcon class="h-4 w-4 fill-current" />
                <span class="inline-block pt-0.5 text-sm leading-6"
                    >Back to Orders</span
                >
            </button>
            <section class="pt-6">
                <h1 class="text-2xl font-bold text-gray-600">Products</h1>
                <div class="grid grid-cols-3 gap-x-6 py-6">
                    <article v-for="product in products">
                        <div
                            class="flex aspect-square items-center justify-center bg-gray-200"
                        >
                            <img :src="product.imgUrl" alt="" />
                        </div>
                        <div>
                            <div class="flex flex-col p-6">
                                <div class="flex items-center justify-between">
                                    <h2 class="font-semibold tracking-wide">
                                        {{ product.name }}
                                    </h2>
                                    <span class="flex items-center gap-x-1">
                                        <Boxicon class="h-4 w-4 text-gray-400 fill-current" />
                                        <Tsherticon class="h-4 w-4 text-gray-400 fill-current" />
                                        <span
                                            class="text-sm font-semibold tracking-wide text-gray-800"
                                            >{{ product.category }}
                                        </span>
                                    </span>
                                </div>
                                <span class="text-sm font-medium text-gray-400"
                                    >Color:
                                    <span class="text-gray-900">{{
                                        product.color
                                    }}</span></span
                                >

                                <a
                                    href="#"
                                    class="mt-6 inline-block text-center text-sm font-semibold text-blue-500 hover:text-blue-600"
                                >
                                    View Mockups
                                </a>
                            </div>
                        </div>
                    </article>
                </div>
            </section>
        </main>
        <aside class="w-72 border-l border-gray-200 ?"></aside>
    </div>
</template>
