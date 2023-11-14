<template>
    <q-layout view="hHh lpR fFf">
        <q-header elevated class="bg-primary text-white" height-hint="98">
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
                <q-route-tab to="/" label="Page One" />
                <q-route-tab to="/page2" label="Page Two" />
                <q-route-tab to="/page3" label="Page Three" />
            </q-tabs>
        </q-header>

        <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
            <!-- drawer content -->
        </q-drawer>

        <q-page-container>
            <!-- <q-router-view /> -->
            <!-- Dropdown -->
            <div class="q-pa-md">
                <q-btn-dropdown color="primary" label="Dropdown Button">
                    <q-list>
                        <q-item clickable v-close-popup @click="onItemClick">
                            <q-item-section>
                                <q-item-label>Photos</q-item-label>
                            </q-item-section>
                        </q-item>

                        <q-item clickable v-close-popup @click="onItemClick">
                            <q-item-section>
                                <q-item-label>Videos</q-item-label>
                            </q-item-section>
                        </q-item>

                        <q-item clickable v-close-popup @click="onItemClick">
                            <q-item-section>
                                <q-item-label>Articles</q-item-label>
                            </q-item-section>
                        </q-item>
                    </q-list>
                </q-btn-dropdown>
            </div>
            <div class="q-pa-md">
                <div class="q-gutter-md row items-start">
                    <!-- <q-date v-model="date" /> -->

                    <q-date v-model="date" landscape />
                </div>
            </div>
        </q-page-container>

        <q-footer elevated class="bg-grey-8 text-white">
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
    </q-layout>
</template>

<script>
import { Inertia } from "@inertiajs/inertia";
import { render } from "vue";
import { ref } from "vue";

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
            getCurrentDateInIST() {
                const options = {
                    timeZone: "Asia/Kolkata", // 'Asia/Kolkata' is the time zone for Indian Standard Time (IST)
                    year: "numeric",
                    month: "numeric",
                    day: "numeric",
                };

                return new Date().toLocaleDateString("en-IN", options);
            },
        };
    },
};
</script>
