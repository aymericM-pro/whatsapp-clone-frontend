<script lang="ts" setup>
import ChatContainer from "../components/ChatContainer.component.vue";
import { ref } from "vue";

const conversations = ref([
    {
        id: "1",
        pseudo: "Papa",
        avatarUrl: "",
        lastMessageSend:
            "peut-être qu’on risque de faire pareille 🥹 mais comme on rajoutera les uniformes et interdira les téléphones on aura l’impression d’avancer 🤔",
        hourMessageSend: "15:58",
        active: false,
    },
    {
        id: "1",
        pseudo: "Tom",
        avatarUrl: "",
        lastMessageSend:
            "peut-être qu’on risque de faire pareille 🥹 mais comme on rajoutera les uniformes et interdira les téléphones on aura l’impression d’avancer 🤔",
        hourMessageSend: "15:58",
        active: false,
    },
    {
        id: "1",
        pseudo: "John",
        avatarUrl: "",
        lastMessageSend:
            "peut-être qu’on risque de faire pareille 🥹 mais comme on rajoutera les uniformes et interdira les téléphones on aura l’impression d’avancer 🤔",
        hourMessageSend: "15:58",
        active: false,
    },
    {
        id: "1",
        pseudo: "Famille",
        avatarUrl: "",
        lastMessageSend:
            "peut-être qu’on risque de faire pareille 🥹 mais comme on rajoutera les uniformes et interdira les téléphones on aura l’impression d’avancer 🤔",
        hourMessageSend: "15:58",
        active: false,
    },
    {
        id: "1",
        pseudo: "soeur",
        avatarUrl: "",
        lastMessageSend:
            "peut-être qu’on risque de faire pareille 🥹 mais comme on rajoutera les uniformes et interdira les téléphones on aura l’impression d’avancer 🤔",
        hourMessageSend: "15:58",
        active: false,
    },
    {
        id: "1",
        pseudo: "Mere",
        avatarUrl: "",
        lastMessageSend:
            "peut-être qu’on risque de faire pareille 🥹 mais comme on rajoutera les uniformes et interdira les téléphones on aura l’impression d’avancer 🤔",
        hourMessageSend: "15:58",
        active: false,
    },
    {
        id: "1",
        pseudo: "Paris",
        avatarUrl: "",
        lastMessageSend:
            "peut-être qu’on risque de faire pareille 🥹 mais comme on rajoutera les uniformes et interdira les téléphones on aura l’impression d’avancer 🤔",
        hourMessageSend: "15:58",
        active: false,
    },
    {
        id: "1",
        pseudo: "cours",
        avatarUrl: "",
        lastMessageSend:
            "peut-être qu’on risque de faire pareille 🥹 mais comme on rajoutera les uniformes et interdira les téléphones on aura l’impression d’avancer 🤔",
        hourMessageSend: "15:58",
        active: false,
    },
]);

const getAvatarColor = (name: string) => {
    const colors = [
        "bg-red-700",
        "bg-pink-700",
        "bg-purple-700",
        "bg-indigo-700",
        "bg-blue-700",
        "bg-teal-700",
        "bg-green-700",
        "bg-yellow-700",
        "bg-orange-700",
        "bg-amber-700",
        "bg-lime-700",
        "bg-rose-700",
    ];
    let hash = 0;

    for (let i = 0; i < name.length; i++) {
        hash = name.charCodeAt(i) + ((hash << 5) - hash);
    }

    return colors[Math.abs(hash) % colors.length];
};
</script>

<template>
    <div class="flex w-full">
        <div class="bg-surface w-[500px] px-4 h-screen flex flex-col">
            <div class="flex items-center justify-between">
                <h1 class="text-white py-3 text-xl semi-bold">Discussion</h1>
                <i class="mdi mdi-square-edit-outline text-2xl py-3 text-white"></i>
            </div>

            <div class="relative">
                <i
                    class="mdi mdi-magnify absolute left-3 top-1/2 -translate-y-1/2 text-gray-400 text-base"
                ></i>
                <input
                    class="w-full bg-transparent text-white placeholder:text-gray-400 pl-10 pr-3 py-1.5 rounded-md border border-gray-600 focus:outline-none focus:ring-1 focus:ring-gray-400"
                    placeholder="Rechercher"
                    type="text"
                />
            </div>

            <div class="flex-1 mt-2 overflow-y-auto space-y-1 pr-1">
                <div
                    v-for="(conversation, index) in conversations"
                    :key="index"
                    class="flex items-center gap-3 py-2 px-4 hover:bg-hoverEffect rounded-lg cursor-pointer"
                >
                    <!-- AVATAR -->
                    <div class="shrink-0">
                        <img
                            v-if="conversation.avatarUrl"
                            :src="conversation.avatarUrl"
                            alt="avatar"
                            class="w-10 h-10 rounded-full object-cover"
                        />
                        <div
                            v-else
                            :class="[
                                'w-10 h-10 rounded-full flex items-center justify-center text-white',
                                getAvatarColor(conversation.pseudo),
                            ]"
                        >
                            <i class="mdi mdi-account text-lg"></i>
                        </div>
                    </div>

                    <!-- TEXTE -->
                    <div class="flex justify-between items-center w-full">
                        <div class="flex flex-col w-[250px]">
                            <h3 class="text-white font-medium">{{ conversation.pseudo }}</h3>
                            <p class="text-sm text-gray-400 truncate">
                                {{ conversation.lastMessageSend }}
                            </p>
                        </div>
                        <span class="text-xs text-gray-400">{{
                            conversation.hourMessageSend
                        }}</span>
                    </div>
                </div>
            </div>
        </div>
        <ChatContainer class="w-full" />
    </div>
</template>
