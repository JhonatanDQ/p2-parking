<script setup>
import { ref } from 'vue';

const total = ref(52600);

const boxes = ref(Array(24).fill(false));

const hizoClick = (index) => {
    boxes.value[index] = !boxes.value[index]; 
    if (boxes.value[index]) {
        
    } else {
        total.value += 500;
    }
};
</script>

<template>
    <div class="flex container bg-slate-600 text-center justify-center h-12 max-w-[1600px] mx-auto">
        <h1 class="text-center text-white text-3xl font-bold mb-4">
            Parqueadero tarifa
        </h1>
    </div>

    <div class="flex container justify-center max-w-[1600px] mx-auto">
        <div class="container max-w-6xl mx-auto mt-10 grid grid-cols-6 gap-4 h-[300px] w-[1000px]">
            <h1 class="text-center text-2xl font-bold mt-2 col-span-6">
                Motos
            </h1>
            <div
                v-for="(clicked, index) in boxes.slice(0, 6)"
                :key="index"
                @click="hizoClick(index)"
                class="rounded-lg p-4 text-center flex justify-center"
                :class="clicked ? 'bg-red-200 font-bold' : 'bg-lime-200'"
            >
                {{ clicked ? 'Ocupado' : 'Libre' }}
            </div>
        </div>
    </div>

    <div class="flex container justify-center max-w-[1600px] mx-auto">
        <div class="container max-w-6xl mx-auto mt-10 grid grid-cols-6 gap-4 h-[300px] w-[1500px]">
            <h1 class="text-center text-2xl font-bold mt-2 col-span-6">
                Carros
            </h1>
            <div
                v-for="(clicked, index) in boxes.slice(6, 24)"
                :key="index" @click="hizoClick(index + 6)" 
                class="rounded-lg p-4 text-center flex justify-center"
                :class="clicked ? 'bg-red-200 font-bold' : 'bg-lime-200'"
            >
                {{ clicked ? 'Ocupado' : 'Libre' }}
            </div>
        </div>
    </div>

    <div class="mt-12 flex container max-w-[1600px] mx-auto h-24">
        <h1 class="text-4xl font-semibold">
            Total: ${{ total }}
        </h1>
    </div>
</template>
