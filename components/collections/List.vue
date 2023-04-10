<template>
    <ul role="list" class="grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-3">
      <li v-for="(data,index) in carddata" :key="index" class="col-span-1 divide-y divide-gray-200 rounded-lg bg-white shadow">
        <div class="flex w-full items-center justify-between space-x-6 p-6">
          <div class="flex-1 truncate">
            <div class="flex items-center space-x-3">
              <h3 class="truncate text-sm font-medium text-gray-900">{{ data.nameGetItemValue }}</h3>
            </div>
            <p class="mt-1 truncate text-sm text-gray-500">{{ data.ageGetItemValue }}</p>
            <p class="mt-1 truncate text-sm text-gray-500">{{ data.genderGetItemValue }}</p>
            <p class="mt-1 truncate text-sm text-gray-500">{{ data.dateofbirthGetItemValue }}</p>
          </div>
          
          <!-- <img class="h-10 w-10 flex-shrink-0 rounded-full bg-gray-300" :src="person.imageUrl" alt="" /> -->
        </div>
        <div>
          <div class="-mt-px flex divide-x divide-gray-200">
            <div class="flex w-0 flex-1">
                <button type="button" class="px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600" @click="editdata('emiteditdata',data)">
                <PencilSquareIcon class="h-5 w-5 text-gray-400" aria-hidden="true"  />
            </button>
            </div>
            <div class="-ml-px flex w-0 flex-1">
              <a class="relative inline-flex w-0 flex-1 items-center justify-center gap-x-3 rounded-br-lg border border-transparent py-4 text-sm font-semibold text-gray-900">
                <TrashIcon class="h-5 w-5 text-gray-400" aria-hidden="true" />
                
              </a>
            </div>
          </div>
        </div>
      </li>
    </ul>
  </template>
  
  <script setup>
  import { EnvelopeIcon, PhoneIcon, TrashIcon,PencilSquareIcon } from '@heroicons/vue/20/solid'
  import {ref,defineProps,defineEmits} from "vue";
  const props = defineProps({
  // Declare props
  carddata: Array,
});
const editdata = defineEmits(["emiteditdata"])
  </script>