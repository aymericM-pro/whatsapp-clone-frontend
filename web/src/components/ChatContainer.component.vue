<script lang="ts" setup>
import { onMounted, ref, watch } from "vue";
import Message from "./Message.component.vue";

type Msg = {
    text?: string;
    time?: string;
    sent: boolean;
    seen?: boolean;
    emoji?: string;
};

const messages: Msg[] = [
    { text: "Là je suis à Nanterre ville", sent: false, time: "11:09" },
    { text: "Qu’est-ce qu’il a diagnostiqué ?", sent: false, time: "11:09" },
    { text: "Quel document ?", sent: false, time: "11:10" },
    {
        text: "Un coup de stress\nMalheureusement c’est ce que je pensais",
        sent: false,
        time: "11:13",
    },

    { text: "Du zona", sent: true, time: "11:12", seen: true },
    { text: "Le médicament", sent: true, time: "", seen: true },
    {
        text: "Et il a dit que c’est rare pour des gens de mon âge d’en avoir",
        sent: true,
        time: "",
        seen: true,
    },
    { emoji: "😓", sent: true, time: "11:14", seen: true },

    { text: "Des pains hot-dog plus Knacki ?", sent: true, time: "11:29", seen: true },
    { text: "Sinon pas grave", sent: true, time: "11:29", seen: true },
    { text: "Et des ravioles", sent: true, time: "11:29", seen: true },

    {
        text: "Alors\nJ’ai les saucisses pour ce midi car il faut les manger aujourd’hui",
        sent: false,
        time: "11:30",
    },
    { text: "Ok ravioles", sent: false, time: "11:30" },
    { text: "Je vais voir\nTu n’as pas envie de steaks ?", sent: false, time: "11:31" },

    { text: "Mais d’autres pour le weekend possible ?", sent: true, time: "11:30", seen: true },
    { text: "J’en ai eu un hier\nMais pk pas", sent: true, time: "11:31", seen: true },

    { text: "Tu veux du riz ce soir ?", sent: false, time: "11:32" },
    { text: "Non j’ai pris des pâtes", sent: true, time: "11:33", seen: true },
    { text: "Pense à prendre du pain", sent: false, time: "11:34" },
    { text: "Oui je passe à la boulangerie", sent: true, time: "11:34", seen: true },
    { text: "Tu veux dessert ?", sent: false, time: "11:35" },
    { text: "Une petite tarte pourquoi pas 😋", sent: true, time: "11:36", seen: true },
    { emoji: "🥧", sent: false, time: "11:37" },
    { text: "Je suis devant Monoprix", sent: false, time: "11:38" },
    { text: "Tu veux quelque chose ?", sent: false, time: "11:38" },
    { text: "Non c’est bon merci ❤️", sent: true, time: "11:39", seen: true },
    { emoji: "😊", sent: false, time: "11:40" },
];
const mainRef = ref<HTMLElement | null>(null);

const scrollToBottom = () => {
    if (mainRef.value) {
        mainRef.value.scrollTop = mainRef.value.scrollHeight;
    }
};

onMounted(() => {
    scrollToBottom();
});

watch(messages, () => scrollToBottom, { deep: true });
</script>

<template>
    <div class="bg-background h-screen flex flex-col text-white overflow-hidden">
        <header
            class="bg-surface/90 backdrop-blur p-2.5 text-sm flex items-center justify-between sticky top-0 z-10"
        >
            <div class="flex items-center gap-3">
                <div
                    class="w-8 h-8 rounded-full bg-orange-600 flex items-center justify-center text-white"
                >
                    P
                </div>
                <div class="flex flex-col">
                    <div class="font-semibold">Papa</div>
                    <div class="text-[11px] text-gray-400">en ligne aujourd'hui à 12:06</div>
                </div>
            </div>

            <div class="flex items-center gap-4 text-gray-300 text-xl">
                <i class="mdi mdi-video-outline cursor-pointer"></i>
                <i class="mdi mdi-phone-outline cursor-pointer"></i>
                <i class="mdi mdi-magnify cursor-pointer"></i>
            </div>
        </header>

        <main ref="mainRef" class="flex-1 overflow-y-auto px-2.5 py-3 space-y-1">
            <Message v-for="(m, i) in messages" :key="i" v-bind="m" />
        </main>

        <footer class="bg-surface p-2">
            <div class="flex items-center gap-2">
                <i class="mdi mdi-plus text-gray-300 text-xl"></i>
                <input
                    class="flex-1 bg-background/70 text-white placeholder:text-gray-400 px-3 py-1.5 rounded-full outline-none text-sm"
                    placeholder="Écrire un message"
                    type="text"
                />
                <i class="mdi mdi-microphone text-gray-300 text-xl"></i>
            </div>
        </footer>
    </div>
</template>
