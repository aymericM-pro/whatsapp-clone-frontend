<script lang="ts" setup></script>

<template>
    <div class="bg-background min-h-screen flex flex-col">
        <header class="bg-surface p-4 text-white">WhatsApp Clone</header>

        <main class="flex-1 p-4 space-y-3">
            <!-- Message reçu -->
            <div class="bg-surface text-text p-3 rounded-lg w-fit max-w-md">Salut 👋</div>

            <!-- Message envoyé -->
            <div class="bg-message text-white p-3 rounded-lg w-fit max-w-md self-end">
                Hello, ça va ?
                <span class="text-seen text-xs ml-2">✓✓</span>
            </div>
        </main>
    </div>
</template>
