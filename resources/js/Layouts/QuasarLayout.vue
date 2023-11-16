<template>
    <q-layout view="hHh lpR fFf">
        <q-header elevated class="text-white bg-primary" height-hint="98">
            <q-toolbar>
                <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

                <q-toolbar-title>
                    <q-avatar>
                        <img
                            src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg"
                        />
                    </q-avatar>
                    Title
                </q-toolbar-title>
            </q-toolbar>
            
            <q-tabs align="left">
                <q-route-tab @click="report"  label="Report" />
                <q-route-tab label="Blogs"  @click="blogs"/>
                <q-route-tab  label="Dashboard" @click="dashboard" />
            </q-tabs>

            
            <div class="q-pa-md ">
                <q-btn-dropdown color="primary" :label="$page.props.auth.user.name">
                    <q-list>
                        <q-item clickable v-close-popup >
                            <q-item-section>
                                        <Link
                                            :href="route('profile.edit')"
                                        >
                                            Profile
                                         </Link>
                                
                            </q-item-section>
                        </q-item>

                        <q-item clickable v-close-popup >
                            <q-item-section>
                                    <Link
                                            :href="route('logout')"
                                            method="post"
                                            
                                        >
                                            Logout
                                    </Link>
                            </q-item-section>
                        </q-item>

                    </q-list>
                </q-btn-dropdown>
            </div>
            
        </q-header>

        <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
            <!-- drawer content -->
        </q-drawer>

        <q-page-container>
            <slot></slot>
            <!-- Dropdown -->
            
            
        </q-page-container>

        <q-footer elevated class="text-white bg-grey-8">
            <q-toolbar>
                <q-toolbar-title>
                    <q-avatar>
                        <img
                            src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg"
                        />
                    </q-avatar>
                    <div>Title</div>
                </q-toolbar-title>
            </q-toolbar>
        </q-footer>
          <!-- Page Heading -->
          <header class="bg-white shadow" v-if="$slots.header">
                <div class="px-4 py-6 mx-auto max-w-7xl sm:px-6 lg:px-8">
                    <slot name="header" />
                </div>
            </header>

            <!-- Page Content -->
            <!-- <main>
                <slot />
            </main> -->
            
    </q-layout>
</template>

<!-- <script>
import { Inertia } from "@inertiajs/inertia";
import { router } from '@inertiajs/vue3'
import { render } from "vue";
import { ref } from "vue";
import DropdownLink from "@/Components/DropdownLink.vue";
import NavLink from "@/Components/NavLink.vue";
import { Link, usePage } from "@inertiajs/vue3";
export default {
    setup() {
        const leftDrawerOpen = ref(false);
        // const date = this.getCurrentDateInIST();
        return {
            leftDrawerOpen,
            date: ref(""),
            toggleLeftDrawer() {
                leftDrawerOpen.value = !leftDrawerOpen.value;
            },
            onItemClick() {
                console.log("I Was clicked");
            },
           
            // Redirect to a route without inertia
            dosomething(){
                router.visit('/dashboard')
            }
        };
    },
};
</script> -->
<script setup>
import { Inertia } from "@inertiajs/inertia";
import { router } from '@inertiajs/vue3'
import { render } from "vue";
import { ref } from "vue";
import DropdownLink from "@/Components/DropdownLink.vue";
import NavLink from "@/Components/NavLink.vue";
import { Link, usePage } from "@inertiajs/vue3";
// Your other imports

const leftDrawerOpen = ref(false);
const date = ref("");

const toggleLeftDrawer = () => {
  leftDrawerOpen.value = !leftDrawerOpen.value;
};

const onItemClick = () => {
  console.log("I Was clicked");
};

// Redirect to a route using Inertia
const blogs = () => {
  // Use Inertia to visit the dashboard route
  router.visit('/blogs');
};
const report = () => {
  // Use Inertia to visit the dashboard route
  router.visit('/report');
};
const dashboard = () => {
  // Use Inertia to visit the dashboard route
  router.visit('/quasar');
};




</script>