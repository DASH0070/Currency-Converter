<script setup lang="ts">

import { ref } from 'vue';

const converion: { [key: string]: [number, string] } = {
    KWD: [0.31, 'Kuwaiti Dinar'],
    BHD: [0.38, 'Bahraini Dinar'],
    OMR: [0.39, 'Omani Rial'],
    BP: [0.88, 'British Pound Sterling'],
    EUR: [1.01, 'European Euro'],
    USD: [1.00, 'US Dollar'],
    BND: [1.43, 'Brunei Dollar'],
    NZD: [1.74, 'New Zealand Dollar'],
    AWG: [1.80, 'Aruban Florin'],
    INR: [81.40, 'Indian Rupee']
};
const val1 = ref<number>(1);
const val2 = ref<number>(81.4);
const currency1 = ref<string>('USD');
const currency2 = ref<string>('INR');

const convertCurrency = () => {
    val2.value = val1.value * converion[currency2.value][0] / converion[currency1.value][0];
}

// Exchange LHS and RHS select box values
const exhange = () => {
    let tmpValue = val1.value;
    val1.value = val2.value;
    val2.value = tmpValue;
    let tmpCurrency
    tmpCurrency = currency1.value;
    currency1.value = currency2.value;
    currency2.value = tmpCurrency;
}
console.log(Object.keys(converion))


</script>

<template>

    <div class="flex gap-20 justify-center">
        <div class="flex flex-col w-40">
            <!-- LHS DROPDOWN -->
            <select id="firstCurrency" v-model="currency1" class="w-40 h-6">
                <option v-for="(curr, index) in converion" :value="index" :key="index">{{curr[1]}}</option>
            </select>
            <input v-model="val1" type="number" class="border-2" />
        </div>
        <!-- EXCHANGE BUTTON  -->
        <button @click="exhange">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round"
                    d="M7.5 21L3 16.5m0 0L7.5 12M3 16.5h13.5m0-13.5L21 7.5m0 0L16.5 12M21 7.5H7.5" />
            </svg>
        </button>

        <div class="flex flex-col w-40">
            <!-- RHS DROPDOWN  -->
            <select id="secondCurrency" v-model="currency2" class="w-40 h-6">
                <option v-for="(curr, index) in converion" :value="index" :key="index">{{curr[1]}}</option>
            </select>
            <input v-model="val2" type="number" class="border-2" />
        </div>
    </div>
    <!-- CONVER CURRENCY BUTTON  -->
    <button @click="convertCurrency"
        class="w-20 border-2 h-8 mx-auto bg-slate-700 text-slate-100 rounded-full block my-10">Convert</button>

</template>