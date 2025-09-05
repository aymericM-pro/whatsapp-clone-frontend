<script lang="ts" setup>
interface Props {
    text?: string;
    time?: string;
    sent?: boolean;
    seen?: boolean;
    emoji?: string;
}

const p = withDefaults(defineProps<Props>(), {
    text: "",
    time: "",
    sent: false,
    seen: false,
    emoji: "",
});
</script>

<template>
    <div></div>
    <div :class="['w-full flex', p.sent ? 'justify-end' : 'justify-start']">
        <div
            :class="[
                'relative max-w-[68%] px-2.5 py-1.5 text-[13px] leading-tight shadow-sm',
                'pr-10', // réserve la place du timestamp
                p.sent
                    ? 'bg-message text-white rounded-2xl rounded-tr-md'
                    : 'bg-surface text-gray-200 rounded-2xl rounded-tl-md',
            ]"
        >
            <template v-if="!p.emoji">
                <div class="whitespace-pre-line break-words">
                    {{ p.text }}
                </div>

                <!-- timestamp + checks en overlay bas-droite -->
                <span
                    :class="p.sent ? 'text-white/80' : 'text-gray-400/90'"
                    class="absolute bottom-1 right-2 flex items-center gap-1 text-[10px]"
                >
                    <span>{{ p.time }}</span>
                    <i
                        v-if="p.seen"
                        :class="p.sent ? 'text-seen' : ''"
                        class="mdi mdi-check-all"
                    ></i>
                </span>
            </template>

            <template v-else>
                <div class="text-xl leading-none">{{ p.emoji }}</div>
                <span
                    v-if="p.time || p.seen"
                    :class="p.sent ? 'text-white/80' : 'text-gray-400/90'"
                    class="absolute bottom-1 right-2 flex items-center gap-1 text-[10px]"
                >
                    <span>{{ p.time }}</span>
                    <i
                        v-if="p.seen"
                        class="mdi mdi-check-all"
                        :class="p.sent ? 'text-seen' : ''"
                    ></i>
                </span>
            </template>
        </div>
    </div>
</template>
