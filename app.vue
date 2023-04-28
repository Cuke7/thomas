<template>
    <div class="drawer drawer-mobile">
        <input id="my-drawer-2" type="checkbox" class="drawer-toggle" />
        <div class="drawer-content flex flex-col h-screen">
            <!-- Page content here -->
            <!-- <label for="my-drawer-2" class="btn btn-primary drawer-button lg:hidden">Open drawer</label> -->
            <div class="w-full bg-blue-800 flex items-center p-5 text-white">
                <label for="my-drawer-2" class="lg:hidden">
                    <Bars3Icon class="h-8 w-8 text-white" />
                </label>
                <div class="mx-auto text-xl">
                    My awesome AI app
                </div>
            </div>
            <div class="flex flex-grow overflow-y-auto flex-col p-4">
                <div v-if="messages.length > 0" v-for="message in messages" class="flex w-full lg:my-4 lg:w-1/2 mx-auto">
                    <div v-if="message.sendFromChat" class="bg-blue-900 ml-auto p-2 rounded-xl flex text-white">
                        {{ message.text }}
                    </div>
                    <div v-else class="bg-green-900 mr-auto p-2 rounded-xl flex text-white">
                        {{ message.text }}
                    </div>
                </div>
                <div v-else class="m-auto text-4xl">
                    Chat with my AI!
                </div>
            </div>
            <div class="flex m-4">
                <input type="text" class=" outline-none border-1 border-white flex-1 flex p-2 rounded-full px-4 text-white"
                    placeholder="Enter text" @keyup.enter="sendMessage" v-model="inputMessage" />
                <div class="btn bg-red-800 ml-4 rounded-full" @click="clear()">clear</div>
            </div>
        </div>
        <div class="drawer-side">
            <label for="my-drawer-2" class="drawer-overlay"></label>
            <ul class="menu p-4 w-80 bg-base-100 text-base-content">
                <!-- Sidebar content here -->
                <li><a>Sidebar Item 1</a></li>
                <li><a>Sidebar Item 2</a></li>
            </ul>

        </div>
    </div>


    <!-- <div class="flex h-screen bg-black flex-col font-mono"> -->
    <!-- <div class="w-full bg-blue-800 flex justify-center items-center p-4 text-white text-2xl">
            Some bar
        </div> -->
    <!-- <div class="flex bg-red-400 flex-grow overflow-y-auto flex-col">
            <div v-if="messages.length > 0" v-for="message in messages" class="flex w-full sm:my-4">
                <div v-if="message.sendFromChat" class="bg-blue-400 ml-auto p-2 rounded-xl flex">
                    {{ message.text }}
                </div>
                <div v-else class="bg-green-400 mr-auto p-2 rounded-xl flex">
                    {{ message.text }}
                </div>
            </div>
        </div> -->

    <!-- <div class="flex justify-center">
            <input type="text" class="text-black outline-none border-1 border-white flex-1 flex p-2 rounded-md"
                placeholder="Enter text" @keyup.enter="sendMessage" v-model="inputMessage" />
            <div class="text-white flex justify-center items-center ml-2 bg-red-800 py-2 px-4 rounded-md hover:bg-slate-400 cursor-pointer"
                @click="clear()">clear</div>
        </div> -->

    <!-- <div class="h-full w-full sm:w-1/2 flex flex-col p-4 sm:py-16">
            <div class="w-full bg-slate-800 rounded-full p-4 text-white mb-4 ">
                Some bar
            </div>
            <div class="bg-slate-700 text-white flex flex-grow p-4 rounded-t-lg flex-col overflow-y-auto">
                
                <div v-else class="m-auto">Chat with my AI!</div>
            </div>
            <div class="flex mt-4 justify-center">
                <input type="text" class="text-black outline-none border-1 border-white flex-1 flex p-2 rounded-md"
                    placeholder="Enter text" @keyup.enter="sendMessage" v-model="inputMessage" />
                <div class="text-white flex justify-center items-center ml-2 bg-red-800 py-2 px-4 rounded-md hover:bg-slate-400 cursor-pointer"
                    @click="clear()">clear</div>
            </div>
        </div> -->
    <!-- </div> -->
</template>

<script setup lang="ts">
import { ref } from "vue";
import { Bars3Icon } from '@heroicons/vue/24/solid'

const inputMessage = ref("");

const messages = ref<any>([]);

const sendMessage = () => {
    if (inputMessage.value.length > 0) {
        messages.value.push({
            text: inputMessage.value,
            sendFromChat: true,
        });
    }
    inputMessage.value = "";
    sendResponse();
};

const sendResponse = () => {
    messages.value.push({
        text: "Hello human!",
        sendFromChat: false,
    });
};

const clear = () => {
    messages.value = [];
};
</script>
