<script setup lang="ts">

import { ref } from 'vue';

const converion: { [key: string]: number } = { KWD: 0.31, BHD: 0.38, OMR: 0.39, GBP: 0.88, EUR: 1.01, USD: 1.00, BND: 1.43, NZD: 1.74, AWG: 1.80, INR: 81.40 };
const val1 = ref<number>(1);
const val2 = ref<number>(81.4);
const currency1 = ref<string>('USD');
const currency2 = ref<string>('INR');

const convertCurrency = () => {
    val2.value = val1.value * converion[currency2.value] / converion[currency1.value];
}

const exhange = () => {
    let tmp: string | number = val1.value;
    val1.value = val2.value;
    val2.value = tmp;
    tmp = currency1.value;
    currency1.value = currency2.value;
    currency2.value = tmp;
}


</script>

<template>

    <div class="flex gap-20 justify-center">
        <div class="flex flex-col w-40">
            <select id="firstCurrency" v-model="currency1" class="w-40 h-6">
                <option value="KWD">Kuwaiti Dinar</option>
                <option value="BHD">Bahraini Dinar</option>
                <option value="OMR">Omani Rial</option>
                <option value="GBP">British Pound Sterling</option>
                <option value="EUR">European Euro</option>
                <option value="USD">US Dollar</option>
                <option value="BND">Brunei Dollar</option>
                <option value="NZD">New Zealand Dollar</option>
                <option value="AWG">Aruban Florin</option>
                <option value="INR">Indian Rupee</option>
            </select>
            <input v-model="val1" type="number" class="border-2" />
        </div>
        <button @click="exhange">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round"
                    d="M7.5 21L3 16.5m0 0L7.5 12M3 16.5h13.5m0-13.5L21 7.5m0 0L16.5 12M21 7.5H7.5" />
            </svg>
        </button>

        <div class="flex flex-col w-40">
            <select id="secondCurrency" v-model="currency2" class="w-40 h-6">
                <option value="KWD">Kuwaiti Dinar</option>
                <option value="BHD">Bahraini Dinar</option>
                <option value="OMR">Omani Rial</option>
                <option value="GBP">British Pound Sterling</option>
                <option value="EUR">European Euro</option>
                <option value="USD">US Dollar</option>
                <option value="BND">Brunei Dollar</option>
                <option value="NZD">New Zealand Dollar</option>
                <option value="AWG">Aruban Florin</option>
                <option value="INR">Indian Rupee</option>
            </select>
            <input v-model="val2" type="number" class="border-2" />
        </div>
    </div>
    <button @click="convertCurrency"
        class="w-20 border-2 h-8 mx-auto bg-slate-700 text-slate-100 rounded-full block my-10">Convert</button>

</template>