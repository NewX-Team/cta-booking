<script setup>
import Checkbox from "@/Components/Checkbox.vue";
import InputError from "@/Components/InputError.vue";
import PrimaryButton from "@/Components/PrimaryButton.vue";
import TextInput from "@/Components/TextInput.vue";
import { Head, Link, useForm } from "@inertiajs/vue3";

defineProps({
    canResetPassword: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});

const form = useForm({
    email: "",
    password: "",
    remember: false,
});

const submit = () => {
    form.post(route("login"), {
        onFinish: () => form.reset("password"),
    });
};
</script>

<template>
    <div
        class="min-h-screen flex items-center justify-center bg-gradient-to-r from-purple-500 to-blue-500"
    >
        <Head title="Log in" />

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

            <!-- Status Message -->
            <div v-if="status" class="mb-4 text-sm text-green-600 text-center">
                {{ status }}
            </div>

            <!-- Login Form -->
            <form @submit.prevent="submit">
                <div class="mb-4">
                    <TextInput
                        id="email"
                        type="email"
                        class="block w-full border-gray-300 rounded-lg focus:ring-purple-500 focus:border-purple-500 transition duration-300 transform focus:scale-105"
                        v-model="form.email"
                        placeholder="Email"
                        required
                        autofocus
                    />
                    <InputError class="mt-2" :message="form.errors.email" />
                </div>

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

                <div class="mb-4 flex items-center justify-between">
                    <label class="flex items-center">
                        <Checkbox
                            name="remember"
                            v-model:checked="form.remember"
                        />
                        <span class="ms-2 text-sm text-gray-600"
                            >Remember me</span
                        >
                    </label>
                    <Link
                        v-if="canResetPassword"
                        :href="route('password.request')"
                        class="text-sm text-purple-500 hover:underline"
                    >
                        Forgot password?
                    </Link>
                </div>

                <div class="mb-4">
                    <PrimaryButton
                        class="w-full justify-center bg-gradient-to-r from-purple-500 to-blue-500 text-white font-semibold py-2 rounded-lg shadow-md hover:shadow-lg hover:scale-105 transition duration-300 transform"
                        :class="{ 'opacity-50': form.processing }"
                        :disabled="form.processing"
                    >
                        Log in
                    </PrimaryButton>
                </div>
            </form>

            <!-- Divider -->
            <div class="flex items-center my-4">
                <div class="flex-grow h-px bg-gray-300"></div>
                <span class="px-2 text-sm text-gray-400">OR</span>
                <div class="flex-grow h-px bg-gray-300"></div>
            </div>

            <!-- Register Link -->
            <div class="text-center">
                <p class="text-sm text-gray-600">
                    Don't have an account?
                    <Link
                        href="/register"
                        class="text-purple-500 hover:underline"
                        >Sign up</Link
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
