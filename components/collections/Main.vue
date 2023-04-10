<template>
    <div class="pb-3 w-[100%]">
        <button type="button"
            class="float-right block rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
            @click="adddetails()">Add Details</button>
        <collectionsAdd v-if="open" :open="open" :key="renderadd" @emitsavedata="senddatacard" />
        <CollectionsList @emiteditdata="emiteditdatacard" :carddata="carddata" :key="renderedit"></CollectionsList>
        <div v-if="openEditcard">
            <CollectionsEdit :editsavedata="editsavedata" @savedatakey="savedatakeycard"></CollectionsEdit>
        </div>
    </div>
</template>
<script setup lang="ts">
import { ref } from "vue"
const open = ref(false)
const openEditcard = ref(false)
const renderadd = ref(0)
const renderedit = ref(0)
const carddata = ref([])
const cardindex = ref(0);
const editsavedata = ref({})
const adddetails = () => {
    open.value = true
    renderadd.value++
}
const senddatacard = (body: Object) => {
    carddata.value.unshift(body)
    console.log("body", body)
}
const emiteditdatacard = (data) => {
    openEditcard.value = true
    renderedit.value++
    editsavedata.value = data
}
const savedatakeycard =(body) =>{
    carddata.value[cardindex.value].unshift(body)
}
</script>
