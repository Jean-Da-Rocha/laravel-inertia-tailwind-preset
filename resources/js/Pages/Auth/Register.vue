<script setup lang="ts">
import { Link, useForm } from '@inertiajs/vue3';
import route from 'ziggy-js';
import Label from '@/Components/Label.vue';
import Input from '@/Components/Input.vue';

const form = useForm<{
  name: string | null;
  email: string | null;
  password: string | null;
  password_confirmation: string | null;
}>({
  name: null,
  email: null,
  password: null,
  password_confirmation: null,
});

const submit = () => form.post(route('register'));
</script>

<template>
  <section class="bg-gray-50 mt-12">
    <div class="flex flex-col items-center justify-center px-6 py-8 mx-auto md:h-screen lg:py-0">
      <div class="w-full bg-white rounded-lg shadow md:mt-0 sm:max-w-md xl:p-0">
        <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
          <h1 class="text-xl font-bold leading-tight tracking-tight text-gray-900 md:text-2xl">Create an account</h1>
          <form class="space-y-4 md:space-y-6" @submit.prevent="submit">
            <div>
              <Label for="name" :input-error-message="form.errors.name">Name</Label>
              <Input
                input-name="name"
                placeholder="John Doe"
                :input-error-message="form.errors.name"
                v-model="form.name"
              />
            </div>
            <div>
              <Label for="email" :input-error-message="form.errors.email">Email</Label>
              <Input
                input-name="email"
                input-type="email"
                placeholder="name@company.com"
                :input-error-message="form.errors.email"
                v-model="form.email"
              />
            </div>
            <div>
              <Label for="password" :input-error-message="form.errors.password">Password</Label>
              <Input
                input-name="password"
                input-type="password"
                placeholder="••••••••"
                :input-error-message="form.errors.password"
                v-model="form.password"
              />
            </div>
            <div>
              <Label for="confirm_password" :input-error-message="form.errors.password_confirmation">
                Confirm Password
              </Label>
              <Input
                input-name="confirm_password"
                input-type="password"
                placeholder="••••••••"
                :input-error-message="form.errors.password_confirmation"
                v-model="form.password_confirmation"
              />
            </div>
            <button
              type="submit"
              class="w-full text-white bg-indigo-600 hover:bg-indigo-700 focus:ring-4 focus:outline-none focus:ring-indigo-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center"
            >
              Create an account
            </button>
            <p class="text-sm font-light text-gray-500">
              Already have an account?
              <Link :href="route('login')" class="font-medium text-indigo-600 hover:underline">Login here</Link>
            </p>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>
