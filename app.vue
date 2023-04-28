<template>
    <div class="drawer drawer-mobile">
        <input id="my-drawer-2" type="checkbox" class="drawer-toggle" />
        <div class="drawer-content flex flex-col h-screen">
            <!-- Page content here -->
            <div class="w-full bg-blue-800 flex items-center p-5 text-white">
                <label for="my-drawer-2" class="lg:hidden">
                    <Bars3Icon class="h-8 w-8 text-white" />
                </label>
                <div class="mx-auto text-xl">
                    My awesome AI app
                </div>
            </div>
            <!-- FLEX GROW POUR QUE LA DIV S'ADAPTE A LA HAUTEUR DISPONIBLE -->
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
