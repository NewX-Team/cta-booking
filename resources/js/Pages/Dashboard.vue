<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
</script>

<template>
    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Dashboard
            </h2>
        </template>

        <template #default>
            <Head title="Welcome to Our Company" />

            <div class="min-h-screen bg-gradient-to-r from-purple-500 via-blue-500 to-indigo-500 text-white">
                <!-- Hero Section -->
                <section class="relative flex items-center justify-center min-h-screen text-center">
                    <div class="z-10 max-w-4xl px-6">
                        <h1 class="text-5xl font-extrabold leading-tight md:text-7xl animate-fadeIn">
                            Welcome to <span class="text-yellow-300">Our Company</span>
                        </h1>
                        <p class="mt-4 text-lg md:text-xl">
                            Innovating the future with cutting-edge technology and solutions.
                        </p>
                        <div class="mt-8 flex justify-center gap-4">
                            <button
                                class="px-6 py-3 text-lg font-semibold bg-yellow-300 text-purple-800 rounded-md shadow-md hover:scale-105 hover:bg-yellow-400 transition-all duration-300"
                            >
                                Learn More
                            </button>
                            <button
                                class="px-6 py-3 text-lg font-semibold bg-purple-700 rounded-md shadow-md hover:scale-105 hover:bg-purple-800 transition-all duration-300"
                            >
                                Contact Us
                            </button>
                        </div>
                    </div>
                    <!-- Background Animation -->
                    <div class="absolute inset-0 z-0 overflow-hidden">
                        <div
                            class="absolute w-64 h-64 bg-yellow-400 rounded-full blur-3xl opacity-50 top-10 left-10 animate-bounce"
                        ></div>
                        <div
                            class="absolute w-96 h-96 bg-blue-400 rounded-full blur-3xl opacity-50 bottom-10 right-10 animate-spin"
                        ></div>
                    </div>
                </section>

                <!-- About Section -->
                <section class="py-16 bg-white text-gray-800">
                    <div class="max-w-7xl mx-auto px-6">
                        <h2
                            class="text-4xl font-bold text-center text-gray-800 animate-fadeInUp"
                        >
                            About Us
                        </h2>
                        <p class="mt-4 text-lg text-center">
                            We are a team of passionate innovators delivering
                            exceptional solutions for our clients.
                        </p>
                        <div
                            class="mt-10 grid grid-cols-1 md:grid-cols-3 gap-8"
                        >
                            <div
                                class="p-6 bg-gray-100 rounded-lg shadow-lg hover:shadow-xl transform hover:scale-105 transition-all duration-300"
                            >
                            php artisan filament:install --forms                  <h3 class="text-xl font-semibold mb-2">
                                    Our Vision
                                </h3>
                                <p class="text-gray-600">
                                    To lead the way in technological
                                    innovation and create a better future for
                                    everyone.
                                </p>
                            </div>
                            <div
                                class="p-6 bg-gray-100 rounded-lg shadow-lg hover:shadow-xl transform hover:scale-105 transition-all duration-300"
                            >
                                <h3 class="text-xl font-semibold mb-2">
                                    Our Mission
                                </h3>
                                <p class="text-gray-600">
                                    Deliver top-notch solutions tailored to
                                    our clients' needs and drive global
                                    impact.
                                </p>
                            </div>
                            <div
                                class="p-6 bg-gray-100 rounded-lg shadow-lg hover:shadow-xl transform hover:scale-105 transition-all duration-300"
                            >
                                <h3 class="text-xl font-semibold mb-2">
                                    Our Values
                                </h3>
                                <p class="text-gray-600">
                                    Innovation, integrity, and a commitment
                                    to excellence in everything we do.
                                </p>
                            </div>
                        </div>
                    </div>
                </section>
            </div>
        </template>
    </AuthenticatedLayout>
</template>
