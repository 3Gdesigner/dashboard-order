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
</script>
<template>
    <div class="fonts-sans flex h-screen w-full bg-white text-gray-900">
        <aside class="relative flex w-52 flex-col border-r border-gray-200 px-6 py-4">
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
        <main>
            <button>
                <ArrowLeftIcons class="h-4 w-4 fill-current" />
                <span>Back to Orders</span>
            </button>
        </main>
    </div>
</template>
