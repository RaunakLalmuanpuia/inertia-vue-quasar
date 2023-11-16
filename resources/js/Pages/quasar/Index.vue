<template>
    <QuasarLayout>
        <p>Hello World</p>
        <div class="q-pa-md">
                <div class="items-start q-gutter-md row">
                    <!-- <q-date v-model="date" /> -->
                    <q-date v-model="date" landscape />
                </div>
            </div>
    </QuasarLayout>
        
    
</template>


<script setup>
import {ref} from 'vue'
import QuasarLayout from "@/Layouts/QuasarLayout.vue";

const date = ref("");


</script>
