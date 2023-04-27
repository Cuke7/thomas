<template>
    <div class="flex h-screen items-center justify-center bg-black flex-col font-mono">
        <div class="h-full w-full sm:w-1/2 flex flex-col p-2 sm:py-16">
            <div class="bg-slate-700 text-white flex flex-grow p-4 rounded-t-lg flex-col overflow-y-auto">
                <div v-if="messages.length > 0" v-for="message in messages" class="flex w-full sm:my-4">
                    <div v-if="message.sendFromChat" class="bg-blue-400 ml-auto p-2 rounded-xl flex">
                        {{ message.text }}
                    </div>
                    <div v-else class="bg-green-400 mr-auto p-2 rounded-xl flex">
                        {{ message.text }}
                    </div>
                </div>
                <div v-else class="m-auto">Chat with my AI!</div>
            </div>
            <div class="flex mt-2 justify-center">
                <input type="text" class="text-black outline-none border-1 border-white flex-1 flex p-2 rounded-md" placeholder="Enter text" @keyup.enter="sendMessage" v-model="inputMessage" />
                <div class="text-white flex justify-center items-center ml-2 bg-red-800 py-2 px-4 rounded-md hover:bg-slate-400 cursor-pointer" @click="clear()">clear</div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

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
