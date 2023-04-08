<template>
    <div >
        <div>
            <div class="pb-3 w-[100%]">
                <button type="button"
                    class="block rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                    @click="addlead()">Add Lead</button>
            </div>
            <collectionsList :tableData="tableData">
            </collectionsList>
        </div>
        <collectionsAdd @submittableData="submitTableData" :sidebarData="sidebarDataForm" v-if="open" :open="open"
            :key="render"></collectionsAdd>
            <CollectionsEdit :saveEditData="saveEditData"></CollectionsEdit>
    </div>
</template>
<script setup>
// import { logger } from "@nuxt/kit";
import {ref} from "vue";
const tableDataIndex = ref(0);
// const tableData = ref([])
// const { $bus } = useNuxtApp();
const render = ref(0);
const open = ref(false);
const addlead = () => {
    console.log("open side bar");
    open.value = true
    render.value++
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
// let options = {
//     method: "GET",
//     headers: {
//         "Content-Type": "application/json",
//         Accept: "application/json",
//         Authorization:
//             "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiM2FiNGRhMmU2ZmZlNDFhMThkMjBhY2U5NDM1MjI5MmYiLCJkIjoiMTY4MDA5MSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODMxOTN9.Syb1XQeqr9lBLaIeS2TCyl760cmliwBooz9oRcrGCjo",
//     },
// };
// const { data: tableData } = await useAuthLazyFetch(
//     "https://v1-orm-gharpe.mercury.infinity-api.net/api/leads/?offset=0&limit=100&sort_column=id&sort_direction=desc"
// );
// For add form
const submitTableData = async (form) => {
    // if (form.uid) return updateTableData(form)
    console.log("form main",form)
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
    console.log("tableData",tableData)
    tableData.value.unshift(form);
    console.log("sidebarDataForm", sidebarDataForm)
    sidebarDataForm.value = {};
};
//For Edit form
// const editTableData = async (data, index) => {
//     sidebarDataForm.value = { ...data };
//     tableDataIndex.value = index;
// };

// Updates tableData after edit
// const updateTableData = async (form) => {
//     let options = {
//         method: "PUT",
//         headers: {
//             "Content-Type": "application/json",
//             Accept: "application/json",
//             Authorization:
//                 "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiM2FiNGRhMmU2ZmZlNDFhMThkMjBhY2U5NDM1MjI5MmYiLCJkIjoiMTY4MDA5MSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODMxOTN9.Syb1XQeqr9lBLaIeS2TCyl760cmliwBooz9oRcrGCjo",
//         },
//         body: form,
//     };
//     const { data: addtableData } = await useAuthLazyFetchPut(
//         `"https://v1-orm-lib.mars.hipso.cc/email-templates/${form.uid}"`,
//         options
//     );
//     tableData.value[tableDataIndex.value] = form;
//     sidebarDataForm.value = {};
// };

// Delete Table
// const deleteTableData = async (data, index) => {
//     await useAuthLazyFetchDelete(
//         `https://v1-orm-lib.mars.hipso.cc/email-templates/${data.uid}`,
//     )
//     tableData.value.splice(index, 1)
// }
</script>
  