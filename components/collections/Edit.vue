<template>
    <TransitionRoot as="template" :show="open">
        <Dialog as="div" class="relative z-10" @close="open = false">
            <div class="fixed inset-0" />
            <div class="fixed inset-0 overflow-hidden">
                <div class="absolute inset-0 overflow-hidden">
                    <div class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10">
                        <TransitionChild as="template" enter="transform transition ease-in-out duration-500 sm:duration-700"
                            enter-from="translate-x-full" enter-to="translate-x-0"
                            leave="transform transition ease-in-out duration-500 sm:duration-700" leave-from="translate-x-0"
                            leave-to="translate-x-full">
                            <DialogPanel class="pointer-events-auto w-screen max-w-md">
                                <div class="flex h-full flex-col overflow-y-scroll bg-white shadow-xl">
                                    <div class="bg-indigo-700 py-6 px-4 sm:px-6">
                                        <div class="flex items-center justify-between">
                                            <DialogTitle class="text-base font-semibold leading-6 text-white">Add Lead Form
                                            </DialogTitle>
                                            <div class="ml-3 flex h-7 items-center">
                                                <button type="button"
                                                    class="rounded-md bg-indigo-700 text-indigo-200 hover:text-white focus:outline-none focus:ring-2 focus:ring-white"
                                                    @click="open = false">
                                                    <span class="sr-only">Close Form</span>
                                                    <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                                                </button>
                                            </div>
                                        </div>
                                        <!-- <div class="mt-1">
                                            <p class="text-sm text-indigo-300">Lorem, ipsum dolor sit amet consectetur adipisicing elit aliquam ad hic recusandae soluta.</p>
                                        </div> -->
                                    </div>
                                    <div class="relative flex-1 py-6 px-4 sm:px-6">
                                        <!-- Your content -->
                                        <form>
                                            <div class="space-y-12">
                                                <div class="border-b border-gray-900/10 pb-12">
                                                    <p class="mt-1 text-sm leading-6 text-gray-600">Add Leads by filling the
                                                        form below</p>
                                                </div>
                                                <div class="border-b border-gray-900/10 pb-12">
                                                    <div class="mt-10 grid grid-cols-1 gap-y-8 gap-x-6 sm:grid-cols-6">
                                                        <div class="sm:col-span-3">
                                                            <label for="name"
                                                                class="block text-sm font-medium leading-6 text-gray-900">
                                                                Name</label>
                                                            <div class="mt-2">
                                                                <input type="text" v-model="editSidebarData.name" id="name"
                                                                    autocomplete="given-name"
                                                                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
                                                            </div>
                                                        </div>
                                                        <div class="sm:col-span-3">
                                                            <label for="source"
                                                                class="block text-sm font-medium leading-6 text-gray-900">Source</label>
                                                            <div class="mt-2">
                                                                <input type="text" v-model="editSidebarData.source"
                                                                    name="source" id="source" autocomplete="given-source"
                                                                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
                                                            </div>
                                                        </div>
                                                        <div class="sm:col-span-3">
                                                            <label for="phonenumber"
                                                                class="block text-sm font-medium leading-6 text-gray-900">Phone
                                                                Number</label>
                                                            <div class="mt-2">
                                                                <input type="text" v-model="editSidebarData.phone_number"
                                                                    name="phonenumber" id="phonenumber"
                                                                    autocomplete="given-phonenumber"
                                                                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
                                                            </div>
                                                        </div>
                                                        <div class="sm:col-span-3">
                                                            <label for="first_name"
                                                                class="block text-sm font-medium leading-6 text-gray-900">Email</label>
                                                            <div class="mt-2">
                                                                <input type="text" v-model="editSidebarData.email" name="email"
                                                                    id="email" autocomplete="given-email"
                                                                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
                                                            </div>
                                                        </div>
                                                        <div class="sm:col-span-3">
                                                            <label for="status"
                                                                class="block text-sm font-medium leading-6 text-gray-900">Status</label>
                                                            <div class="mt-2">
                                                                <input type="text" v-model="editSidebarData.status"
                                                                    name="status" id="status" autocomplete="given-status"
                                                                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
                                                            </div>
                                                        </div>
                                                        <div class="sm:col-span-3">
                                                            <label for="buying"
                                                                class="block text-sm font-medium leading-6 text-gray-900">Purpose
                                                                of Buying</label>
                                                            <div class="mt-2">
                                                                <input type="text" v-model="editSidebarData.purpose_of_buying"
                                                                    name="buying" id="buying" autocomplete="family-name"
                                                                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
                                                            </div>
                                                        </div>
                                                        <div class="sm:col-span-3">
                                                            <label for="address"
                                                                class="block text-sm font-medium leading-6 text-gray-900">Address</label>
                                                            <div class="mt-2">
                                                                <input type="text" v-model="editSidebarData.address"
                                                                    name="address" id="address" autocomplete="given-address"
                                                                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
                                                            </div>
                                                        </div>
                                                        <div class="sm:col-span-3">
                                                            <label for="modepayment"
                                                                class="block text-sm font-medium leading-6 text-gray-900">Mode
                                                                of Payment</label>
                                                            <div class="mt-2">
                                                                <input type="text" v-model="editSidebarData.mode_of_payment"
                                                                    name="modepayment" id="modepayment"
                                                                    autocomplete="given-modepayment"
                                                                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
                                                            </div>
                                                        </div>
                                                        <div class="sm:col-span-3">
                                                            <label for="downpayment"
                                                                class="block text-sm font-medium leading-6 text-gray-900">Down
                                                                Payment</label>
                                                            <div class="mt-2">
                                                                <input type="text" v-model="editSidebarData.down_payment"
                                                                    name="downpayment" id="downpayment"
                                                                    autocomplete="given-downpayment"
                                                                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
                                                            </div>
                                                        </div>
                                                        <div class="sm:col-span-3">
                                                            <label for="loanrequired"
                                                                class="block text-sm font-medium leading-6 text-gray-900">Loan
                                                                Required</label>
                                                            <div class="mt-2">
                                                                <input type="text" v-model="editSidebarData.is_loan_required"
                                                                    name="loanrequired" id="loanrequired"
                                                                    autocomplete="given-loanrequired"
                                                                    class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>


                                            <div class="mt-6 flex items-center justify-end gap-x-6">
                                                <button type="submit"
                                                    class="rounded-md bg-indigo-600 py-2 px-3 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                                                    @click.prevent="open=false">
                                                    cancel
                                                </button>
                                                <button type="submit"
                                                    class="rounded-md bg-indigo-600 py-2 px-3 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                                                    @click.prevent="saveEditData()">
                                                    save
                                                </button>
                                            </div>
                                        </form>
                                    </div>
                                </div>
                            </DialogPanel>
                        </TransitionChild>
                    </div>
                </div>
            </div>
        </Dialog>
    </TransitionRoot>
</template>
<script setup>
import { ref,defineEmits,defineProps } from 'vue';
const props = defineProps({editSidebarData:Object})
const emit = defineEmits(["saveEditData"])
const open = ref(true);
const saveEditData = ()=>{ 
    emit("saveEditData",props.editSidebarData)
    open.value=false;
}
</script>