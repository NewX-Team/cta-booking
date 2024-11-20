<script setup>
import Checkbox from "@/Components/Checkbox.vue";
import InputError from "@/Components/InputError.vue";
import PrimaryButton from "@/Components/PrimaryButton.vue";
import TextInput from "@/Components/TextInput.vue";
import { Head, Link, useForm } from "@inertiajs/vue3";

const form = useForm({
    name: "",
    email: "",
    password: "",
    password_confirmation: "",
});

const submit = () => {
    form.post(route("register"), {
        onFinish: () => form.reset("password", "password_confirmation"),
    });
};
</script>

<template>
    <div
        class="min-h-screen flex items-center justify-center bg-gradient-to-r from-purple-500 to-blue-500"
    >
        <Head title="Register" />

        <div
            class="max-w-md w-full bg-white rounded-lg shadow-lg p-8 animate-fadeIn"
        >
            <!-- Logo -->
            <div class="mb-6 text-center animate-bounce">
                <h1
                    class="text-3xl font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-blue-500 to-purple-600"
                >
                    Booking App
                </h1>
            </div>

            <!-- Register Form -->
            <form @submit.prevent="submit">
                <!-- Name -->
                <div class="mb-4">
                    <TextInput
                        id="name"
                        type="text"
                        class="block w-full border-gray-300 rounded-lg focus:ring-purple-500 focus:border-purple-500 transition duration-300 transform focus:scale-105"
                        v-model="form.name"
                        placeholder="Full Name"
                        required
                        autofocus
                    />
                    <InputError class="mt-2" :message="form.errors.name" />
                </div>

                <!-- Email -->
                <div class="mb-4">
                    <TextInput
                        id="email"
                        type="email"
                        class="block w-full border-gray-300 rounded-lg focus:ring-purple-500 focus:border-purple-500 transition duration-300 transform focus:scale-105"
                        v-model="form.email"
                        placeholder="Email"
                        required
                    />
                    <InputError class="mt-2" :message="form.errors.email" />
                </div>

                <!-- Password -->
                <div class="mb-4">
                    <TextInput
                        id="password"
                        type="password"
                        class="block w-full border-gray-300 rounded-lg focus:ring-purple-500 focus:border-purple-500 transition duration-300 transform focus:scale-105"
                        v-model="form.password"
                        placeholder="Password"
                        required
                    />
                    <InputError class="mt-2" :message="form.errors.password" />
                </div>

                <!-- Confirm Password -->
                <div class="mb-4">
                    <TextInput
                        id="password_confirmation"
                        type="password"
                        class="block w-full border-gray-300 rounded-lg focus:ring-purple-500 focus:border-purple-500 transition duration-300 transform focus:scale-105"
                        v-model="form.password_confirmation"
                        placeholder="Confirm Password"
                        required
                    />
                    <InputError class="mt-2" :message="form.errors.password_confirmation" />
                </div>

                <!-- Register Button -->
                <div class="mb-4">
                    <PrimaryButton
                        class="w-full justify-center bg-gradient-to-r from-purple-500 to-blue-500 text-white font-semibold py-2 rounded-lg shadow-md hover:shadow-lg hover:scale-105 transition duration-300 transform"
                        :class="{ 'opacity-50': form.processing }"
                        :disabled="form.processing"
                    >
                        Sign Up
                    </PrimaryButton>
                </div>
            </form>

            <!-- Divider -->
            <div class="flex items-center my-4">
                <div class="flex-grow h-px bg-gray-300"></div>
                <span class="px-2 text-sm text-gray-400">OR</span>
                <div class="flex-grow h-px bg-gray-300"></div>
            </div>

            <!-- Login Link -->
            <div class="text-center">
                <p class="text-sm text-gray-600">
                    Already have an account?
                    <Link
                        href="/login"
                        class="text-purple-500 hover:underline"
                        >Log in</Link
                    >
                </p>
            </div>
        </div>
    </div>
</template>

<style>
@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(-20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}
.animate-fadeIn {
    animation: fadeIn 1s ease-in-out;
}
</style>
