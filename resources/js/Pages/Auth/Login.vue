<script setup lang="ts">
import { Link, useForm } from '@inertiajs/vue3';
import route from 'ziggy-js';
import Label from '@/Components/Label.vue';
import Input from '@/Components/Input.vue';

const form = useForm<{
  email: string | null;
  password: string | null;
  remember_me: boolean | null;
}>({
  email: null,
  password: null,
  remember_me: null,
});

const submit = () => form.post(route('login'));
</script>

<template>
  <section class="bg-gray-50 mt-12">
    <div class="flex flex-col items-center justify-center px-6 py-8 mx-auto md:h-screen lg:py-0">
      <div class="w-full bg-white rounded-lg shadow md:mt-0 sm:max-w-md xl:p-0">
        <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
          <h1 class="text-xl font-bold leading-tight tracking-tight text-gray-900 md:text-2xl">
            Sign in to your account
          </h1>
          <form class="space-y-4 md:space-y-6" @submit.prevent="submit">
            <div>
              <Label for="email" :input-error-message="form.errors.email">Email</Label>
              <Input
                input-name="email"
                input-type="email"
                :input-error-message="form.errors.email"
                v-model="form.email"
                placeholder="your@email.com"
                :required="true"
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
            <div class="flex items-center justify-between">
              <div class="flex items-start">
                <div class="flex items-center h-5">
                  <input
                    id="remember"
                    aria-describedby="remember"
                    type="checkbox"
                    class="w-4 h-4 border border-gray-300 rounded bg-gray-50 focus:ring-3 focus:ring-indigo-300 checked:bg-indigo-600"
                    v-model="form.remember_me"
                    :required="false"
                  />
                </div>
                <div class="ml-3 text-sm">
                  <label for="remember" class="text-gray-500">Remember me</label>
                </div>
              </div>
              <p class="text-sm font-light text-gray-500">
                <Link :href="route('password.request')" class="font-medium text-indigo-600 hover:underline">
                  Forgot password?
                </Link>
              </p>
            </div>
            <button
              type="submit"
              class="w-full text-white bg-indigo-600 hover:bg-indigo-700 focus:ring-4 focus:outline-none focus:ring-indigo-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center"
              :disabled="form.processing"
            >
              Sign in
            </button>
            <p class="text-sm font-light text-gray-500">
              Don't have an account yet?
              <Link :href="route('register')" class="font-medium text-indigo-600 hover:underline">Sign up</Link>
            </p>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>
