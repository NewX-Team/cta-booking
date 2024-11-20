<script setup>
import { Head, Link } from "@inertiajs/vue3";

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
    document.getElementById("screenshot-container")?.classList.add("!hidden");
    document.getElementById("docs-card")?.classList.add("!row-span-1");
    document.getElementById("docs-card-content")?.classList.add("!flex-row");
    document.getElementById("background")?.classList.add("!hidden");
}
</script>

<template>
    <div
        class="min-h-screen flex flex-col items-center justify-between bg-gray-100"
    >
        <!-- Hero Section -->
        <div
            class="text-center py-20 px-4 bg-gradient-to-br from-blue-500 to-purple-600 text-white"
        >
            <h1 class="text-5xl font-bold mb-4">
                Selamat Datang di Aplikasi Kami
            </h1>
            <p class="text-lg mb-6">
                Platform yang mempermudah pengelolaan video streaming dan
                memberikan pengalaman luar biasa.
            </p>
            <div class="flex justify-center space-x-4">
                <Link
                    v-if="canLogin"
                    href="/login"
                    class="px-6 py-3 bg-white text-blue-600 font-semibold rounded-lg shadow hover:bg-gray-200"
                >
                    Login
                </Link>
                <Link
                    v-if="canRegister"
                    href="/register"
                    class="px-6 py-3 bg-purple-700 text-white font-semibold rounded-lg shadow hover:bg-purple-800"
                >
                    Register
                </Link>
            </div>
        </div>
        class
        <!-- Features Section -->
        <div
            class="py-16 px-6 max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-3 gap-8"
        >
            <div class="bg-white rounded-lg shadow p-6 text-center">
                <h3 class="text-xl font-semibold mb-2">Mudah Digunakan</h3>
                <p class="text-gray-600">
                    Antarmuka yang sederhana dan mudah dipahami.
                </p>
            </div>
            <div class="bg-white rounded-lg shadow p-6 text-center">
                <h3 class="text-xl font-semibold mb-2">Fitur Lengkap</h3>
                <p class="text-gray-600">
                    Dilengkapi fitur lengkap untuk kebutuhan Anda.
                </p>
            </div>
            <div class="bg-white rounded-lg shadow p-6 text-center">
                <h3 class="text-xl font-semibold mb-2">Aman & Terpercaya</h3>
                <p class="text-gray-600">
                    Keamanan data Anda adalah prioritas kami.
                </p>
            </div>
        </div>

        <!-- Footer -->
        <footer class="py-4 text-center text-gray-600">
            <p>
                © {{ new Date().getFullYear() }} Aplikasi Kami. Laravel
                {{ laravelVersion }}, PHP {{ phpVersion }}.
            </p>
        </footer>
    </div>
</template>
