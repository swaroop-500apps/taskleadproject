<template>
  <div class="px-4 sm:px-6 lg:px-8">
    <div class="sm:flex sm:items-center">
      <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
      </div>
    </div>
    <div class="mt-8 flow-root">
      <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
          <div class="overflow-hidden shadow ring-1 ring-black ring-opacity-5 sm:rounded-lg">
            <table class="min-w-full divide-y divide-gray-300">
              <thead class="bg-gray-50">
                <tr>
                  <th scope="col" class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-6">Name</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Source</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Phone Number</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Email</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Status</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Purpose of Buying</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Address</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Mode of payment</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Down Payment</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Loan Required</th>
                  <!-- <th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-6">
                    <span class="sr-only">Edit</span>
                  </th>
                  <th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-6">
                  <span class="sr-only">Delete</span>
                </th> -->
                </tr>
                
              </thead>
              <tbody class="divide-y divide-gray-200 bg-white">
                <tr v-for="(data,index) in tableData" :key="index">  
                  <td class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-6">{{ data.name }}
                  </td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ data.source }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ data.phone_number }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ data.email }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ data.status }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ data.purpose_of_buying }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ data.address }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ data.mode_of_payment }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ data.down_payment }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ data.is_loan_required }}</td>
                  <button type="button" class="text-sm font-semibold m-2 leading-6 text-gray-900" @click="editButton('emitEditData',data)">
                    Edit
                  </button>
                  <button type="button"
                    class="rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                    @click="deleteButton()">
                    Delete
                  </button>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
    <collectionsAdd />
  </div>
</template>
    
<script setup>
import {defineProps,defineEmits} from "vue"
const open = ref(false)
const props = defineProps({
  // Declare props
  tableData: Array,
});
const editButton = defineEmits(["emitEditData"])
</script>