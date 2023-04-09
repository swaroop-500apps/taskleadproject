<template>
    <div>
        <div>
            <div class="pb-3 w-[100%]">
                <button type="button"
                    class="float-right block rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                    @click="addlead()">Add Lead</button>
            </div>
            <collectionsList :tableData="tableData" @emitEditData="emitEditData" :key="renderedit">
            </collectionsList>
        </div>
        <collectionsAdd @submittableData="submitTableData" :sidebarData="sidebarDataForm" v-if="open" :open="open"
            :key="renderadd"></collectionsAdd>
        <div v-if="openEditSidebar">
            <CollectionsEdit :editSidebarData="editSidebarData" @saveEditData="saveEditData"></CollectionsEdit>
        </div>
    </div>
</template>
<script setup lang="ts">
// import { logger } from "@nuxt/kit";
import { ref } from "vue";
const tableDataIndex = ref(0);
// const tableData = ref([])
// const { $bus } = useNuxtApp();
const renderedit = ref(0)
const renderadd = ref(0);
const open = ref(false);
const openEditSidebar = ref(false)
const addlead = () => {
    open.value = true
    renderadd.value++
}
const sidebarDataForm = ref({
    name: "",
    source: "",
    phone_number: "",
    email: "",
    status: "",
    purpose_of_buying: "",
    address: "",
    mode_of_payment: "",
    down_payment: "",
    is_loan_required: "",
});

// Get Table Data
let options = {
    method: "GET",
    headers: {
        "Content-Type": "application/json",
        Accept: "application/json",
        Authorization:
            "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiM2FiNGRhMmU2ZmZlNDFhMThkMjBhY2U5NDM1MjI5MmYiLCJkIjoiMTY4MDA5MSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODMxOTN9.Syb1XQeqr9lBLaIeS2TCyl760cmliwBooz9oRcrGCjo",
    },
};
const { data: tableData } = await useAuthLazyFetch(
    "https://v1-orm-gharpe.mercury.infinity-api.net/api/leads/?offset=0&limit=100&sort_column=id&sort_direction=desc"
);
// For add form
const submitTableData = async (form) => {
    // if (form.uid) return updateTableData(form)
    console.log("form main", form)
    let postoptions = {
        method: "POST",
        headers: {
            "Content-Type": "application/json",
            Accept: "application/json",
            Authorization:
                "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiM2FiNGRhMmU2ZmZlNDFhMThkMjBhY2U5NDM1MjI5MmYiLCJkIjoiMTY4MDA5MSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODMxOTN9.Syb1XQeqr9lBLaIeS2TCyl760cmliwBooz9oRcrGCjo",
        },
        body: form,
    };
    const { data: addtableData } = await useAuthLazyFetchPost(
        "https://v1-orm-gharpe.mercury.infinity-api.net/api/leads/",
        postoptions
    );
    tableData.value.unshift(form);
    sidebarDataForm.value = {};
};

//open edit sidebar
const editSidebarData = ref({})
const emitEditData = (data) => {
    openEditSidebar.value = true
    renderedit.value++
    editSidebarData.value = data
}
// Updates tableData after edit
const saveEditData = async (form) => {
    let options = {
        method: "PUT",
        headers: {
            "Content-Type": "application/json",
            Accept: "application/json",
            Authorization:
                "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiM2FiNGRhMmU2ZmZlNDFhMThkMjBhY2U5NDM1MjI5MmYiLCJkIjoiMTY4MDA5MSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODMxOTN9.Syb1XQeqr9lBLaIeS2TCyl760cmliwBooz9oRcrGCjo",
        },
        body: form,
    };
    const { data: addtableData } = await useAuthLazyFetchPut(
        `"https://v1-orm-gharpe.mercury.infinity-api.net/api/leads/${form.uid}"`,
        options
    );
    tableData.value[tableDataIndex.value] = form;
    sidebarDataForm.value = {};
};

</script>
  