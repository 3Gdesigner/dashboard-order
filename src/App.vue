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
import BoxIcon from "./icons/box.svg";
import TshertIcon from "./icons/t-shirt.svg";
import ChevronRightIcon from "./icons/chevron-right.svg";
import InforIcon from "./icons/info.svg";
import { computed } from "vue";

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
        category: "Bulk",
    },
    {
        name: "Bulk Swag",
        imgUrl: "/img/bulk-swag.png",
        status: "ready to review",
        color: "Custom",
        category: "Pack",
    },
];

const orders = [
    { productName: "Swag -- Pack 1/29/2020", price: 75, quantity: 8 },
    { productName: "Tech Pack-- Pack 1/29/2020", price: 26, quantity: 24 },
    { productName: "Bella + Canva Tee", price: 14, quantity: 32 },
    { productName: "Nike Cap", price: 7.6, quantity: 21 },
    { productName: "Swag -- Pack 1/29/2020", price: 75, quantity: 23 },
    { productName: "Preset Pack -- Pack 1/29/2020", price: 30, quantity: 24 },
    { productName: "Swag Pack + Nike cap", price: 18, quantity: 3 },
    { productName: "Pluk Swag -- Pack ", price: 30, quantity: 2 },
];

const formatMoney = (value) =>
    new Intl.NumberFormat("en-us", {
        style: "currency",
        currency: "USD",
    }).format(value);

const totalOrder = computed(() =>
    orders.reduce((total, order) => total + order.price * order.quantity, 0)
);
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
        <main class="flex-1 overflow-y-scroll">
            <div class="flex flex-col px-10 py-4">
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
                                class="flex aspect-square items-center justify-center overflow-hidden rounded-t-2xl bg-gray-200"
                            >
                                <img :src="product.imgUrl" alt="" />
                            </div>
                            <div>
                                <div class="flex flex-col p-6">
                                    <div
                                        class="flex items-center justify-between"
                                    >
                                        <h2 class="font-semibold tracking-wide">
                                            {{ product.name }}
                                        </h2>
                                        <span class="flex items-center gap-x-1">
                                            <BoxIcon
                                                v-if="
                                                    product.category === 'Pack'
                                                "
                                                class="h-4 w-4 fill-current text-gray-400"
                                            />
                                            <TshertIcon
                                                v-else
                                                class="h-4 w-4 fill-current text-gray-400"
                                            />
                                            <span
                                                class="text-sm font-semibold tracking-wide text-gray-800"
                                                >{{ product.category }}
                                            </span>
                                        </span>
                                    </div>
                                    <span
                                        class="text-sm font-medium text-gray-400"
                                        >Color:
                                        <span class="text-gray-600">{{
                                            product.color
                                        }}</span>
                                    </span>

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

                <section class="py-6">
                    <h1 class="text-2xl font-bold text-gray-600">
                        Shipping & Storage
                    </h1>
                    <div class="relative grid grid-cols-2 gap-x-6 pt-6">
                        <div
                            class="relative overflow-hidden rounded-2xl border border-gray-100 p-6"
                        >
                            <div
                                class="itens-center flex justify-between border-b border-gray-100 pb-4"
                            >
                                <h1 class="font-semibold">
                                    Ship Swag to Recipient
                                </h1>
                                <a
                                    href="#"
                                    class="itens-center flex text-sm font-semibold text-blue-500 hover:text-blue-600"
                                >
                                    <span>View Shippments</span>
                                    <ChevronRightIcon
                                        class="h-4 w-4 fill-current"
                                    />
                                </a>
                            </div>
                            <div class="relative grid grid-cols-2 gap-x-4 pt-4">
                                <div>
                                    <div class="text-sm text-gray-600">
                                        Shippmnets Created
                                    </div>
                                    <div class="pt-2 text-lg font-semibold">
                                        350
                                    </div>
                                </div>

                                <div>
                                    <div class="text-sm text-gray-600">
                                        Total Shippments
                                    </div>
                                    <div class="pt-2 text-lg font-semibold">
                                        $1,400.00
                                    </div>
                                </div>
                            </div>
                            <button
                                class="mt-4 rounded-full border border-blue-500 border-b-blue-600 px-5 py-2 text-sm font-semibold leading-relaxed text-blue-500 hover:border-blue-500 hover:bg-blue-500 hover:text-white"
                            >
                                Create Shippment
                            </button>
                            <img
                                src="/img/shipment.png"
                                alt=""
                                class="absolute bottom-0 right-0 w-28"
                            />
                        </div>
                        <div
                            class="relative overflow-hidden rounded-2xl border border-gray-100 p-6"
                        >
                            <div
                                class="itens-center flex justify-between border-b border-gray-100 pb-4"
                            >
                                <h1 class="font-semibold">
                                    Send Swag to Recipient
                                </h1>
                                <a
                                    href="#"
                                    class="itens-center flex text-sm font-semibold text-blue-500 hover:text-blue-600"
                                >
                                    <span>View SwagUp Storage</span>
                                    <ChevronRightIcon
                                        class="h-4 w-4 fill-current"
                                    />
                                </a>
                            </div>
                            <div class="relative grid grid-cols-2 gap-x-4 pt-4">
                                <div>
                                    <div class="text-sm text-gray-600">
                                        Shippmnets Created
                                    </div>
                                    <div class="pt-2 text-lg font-semibold">
                                        350
                                    </div>
                                </div>

                                <div>
                                    <div class="text-sm text-gray-600">
                                        Total Shippments
                                    </div>
                                    <div class="pt-2 text-lg font-semibold">
                                        $1,400.00
                                    </div>
                                </div>
                            </div>
                            <button
                                class="mt-4 rounded-full border border-blue-500 border-b-blue-600 px-5 py-2 text-sm font-semibold leading-relaxed text-blue-500 hover:border-blue-500 hover:bg-blue-500 hover:text-white"
                            >
                                Update Shippment
                            </button>
                            <img
                                src="/img/storage.png"
                                alt=""
                                class="absolute bottom-0 right-0 w-28"
                            />
                        </div>
                    </div>
                </section>
            </div>
        </main>
        <aside class="w-72 border-l border-gray-200">
            <div class="border-b border-gray-200 px-6 py-4">
                <h5 class="font-semibold leading-relaxed text-gray-800">
                    Order #22353 Sumary
                </h5>
                <p class="text-xs leading-loose text-gray-400">
                    Order Placed: 12-30-2020
                </p>
            </div>

            <ul class="px-6">
                <li
                    v-for="order in orders"
                    class="border-b border-gray-200 py-2"
                >
                    <div class="mt-2 text-sm font-semibold text-gray-800">
                        {{ order.productName }}
                    </div>
                    <div
                        class="mt-1 flex items-center justify-between text-xs text-gray-400"
                    >
                        <span
                            >{{ formatMoney(order.price) }} x
                            {{ order.quantity }}</span
                        >
                        <span class="font-semibold text-gray-800">
                            {{ formatMoney(order.price * order.quantity) }}
                        </span>
                    </div>
                    <a
                        href="#"
                        class="mt-2 inline-block text-xs font-semibold leading-relaxed text-blue-500 hover:text-blue-600"
                        >Edit breakdwon</a
                    >
                </li>
            </ul>
            <div class="border-t border-gray-200 px-6 pb-4">
                <div class="py-2">
                    <div class="itens-center flex justify-between">
                        <div class="text-xs text-gray-400">Subtotal</div>
                        <span class="font-semibold">{{
                            formatMoney(totalOrder)
                        }}</span>
                    </div>
                    <div class="itens-center flex justify-between">
                        <div
                            class="flex items-center gap-x-1 text-xs text-gray-400"
                        >
                            <span> Shippings</span>
                            <InforIcon class="h-4 w-4" />
                        </div>
                        <span>TDB</span>
                    </div>
                    <div class="itens-center flex justify-between">
                        <div
                            class="flex items-center gap-x-1 text-xs text-gray-400"
                        >
                            <span>Warehouse</span>
                            <InforIcon class="h-4 w-4" />
                        </div>
                        <span>TDB</span>
                    </div>
                </div>
                <div
                    class="itens-center flex justify-between border-t border-gray-200 py-4"
                >
                    <div class="text-sm text-gray-400">Total</div>
                    <div class="text-lg font-semibold">
                        {{ formatMoney(totalOrder) }}
                    </div>
                </div>
                <button
                    class="flex w-full items-center justify-center rounded-2xl bg-blue-500 py-4 text-sm font-semibold text-white hover:bg-blue-600"
                >
                    Continue
                </button>
            </div>
        </aside>
    </div>
</template>
