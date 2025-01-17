<script setup>
import { Head, Link } from '@inertiajs/vue3';
import '../../css/app.css';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});

function handleImageError() {
    document.getElementById('screenshot-container')?.classList.add('!hidden');
    document.getElementById('docs-card')?.classList.add('!row-span-1');
    document.getElementById('docs-card-content')?.classList.add('!flex-row');
    document.getElementById('background')?.classList.add('!hidden');
}
</script>

<template>
    <div class="min-h-screen flex flex-col items-center justify-center bg-slate-600 dark:bg-gray-900 bg-custom">
        <Head title="Bienvenido" />
        <div class="max-w-6xl mx-auto sm:px-6 lg:px-8">
            <div class="flex justify-center pt-8 sm:justify-start sm:pt-0">
                <h1 class="text-4xl font-bold text-white/80 dark:text-gray-200">
                    Bienvenido a la app de búsqueda de Pokémon
                    <span v-if="auth && auth.user">{{ auth.user.name }}</span>
                </h1>
            </div>

            <div class="mt-8 bg-white dark:bg-gray-800 overflow-hidden shadow sm:rounded-lg">
                <div class="grid grid-cols-1 md:grid-cols-2">
                    <div class="p-6">
                        <div class="text-center">
                            <div class="ml-4 text-lg leading-7 font-semibold">
                                <Link
                                    v-if="canLogin"
                                    :href="route('login')"
                                    class="rounded-md px-3 py-2 text-black text-center ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                                >
                                    Iniciar sesión
                                </Link>
                            </div>
                        </div>
                    </div>

                    <div class="p-6 border-t border-gray-200 dark:border-gray-700 md:border-t-0 md:border-l">
                        <div class="text-center">
                            <div class="ml-4 text-lg text-center leading-7 font-semibold">
                                <Link
                                    v-if="canRegister"
                                    :href="route('register')"
                                    class="rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                                >
                                    Registrar una cuenta
                                </Link>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
