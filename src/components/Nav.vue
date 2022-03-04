<script setup>
import useAuth from "../composable/useAuth";
const {isAuthenticated, logout} = useAuth();
</script>
<template>
    <div class="text-green-200 bg-green-800">
        <div class="container flex items-center justify-between mx-auto " >
            <h1 class="text-3xl font-thin tracking-tighter">Vue<span class="font-normal">FakeAuth</span></h1>
            <nav>
                <ul class="flex w-full space-x-4">
                    <router-link to="/">
                        <li class="px-4 py-8 hover:cursor-pointer hover:bg-blue-100 hover:text-blue-800">
                            Home 
                        </li>
                    </router-link>
                    <router-link to="/about">
                        <li class="px-4 py-8 hover:cursor-pointer hover:bg-blue-100 hover:text-blue-800">
                            About
                        </li>
                    </router-link>
                    <router-link v-if="!isAuthenticated" to="/login">
                        <li class="px-4 py-8 hover:cursor-pointer hover:bg-blue-100 hover:text-blue-800">
                            Login
                        </li>
                    </router-link>
                    <div v-else class="flex">
                        <router-link to="/secret">
                            <li class="px-4 py-8 hover:cursor-pointer hover:bg-blue-100 hover:text-blue-800">
                                Secret
                            </li>
                        </router-link>
                        <button  @click="logout">
                            <li class="px-4 py-8 hover:cursor-pointer hover:bg-blue-100 hover:text-blue-800">
                                Logout
                            </li>
                        </button>
                    </div>
                </ul>
            </nav>
        </div>
    </div>
</template>