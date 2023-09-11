<template>
    <h1 class="text-lg mb-2">Create</h1>
    <div class="mb-8">
    <Link :href="route('post.index')" class="text-sky-500 text-sm mb-8">Back</Link>
    </div>
    <form @submit.prevent="store">
        <div class="mb-4">
            <input v-model="title" class="w-full rounded-full border-gray-300" type="text" placeholder="title">
            <div v-if="errors.title" class="text-red-600 text-sm">{{ errors.title }}</div>
        </div>
        <div class="mb-4">
            <textarea v-model="content" class="w-full rounded-full border-gray-300" type="text" placeholder="content"></textarea>
            <div v-if="errors.content" class="text-red-600 text-sm">{{ errors.content }}</div>
        </div>
        <div class="mb-4">
            <button class=" hover:text-sky-500 hover:bg-white block ml-auto p-2 w-32 bg-sky-500 border border-sky-500 rounded-full text-center text-white" type="submit">Store</button>
        </div>
    </form>
</template>

<script>
import {Link} from "@inertiajs/vue3";
import axios from "axios";
import MainLayout from "@/Layouts/MainLayout.vue";


export default {
    name: "Create",

    layout: MainLayout,

    props: [
        'errors'
    ],

    data() {
        return {
            title: '',
            content: '',
        }
    },

    components: {
        Link
    },

    methods: {
        store() {
            this.$inertia.post('/posts', {title: this.title, content: this.content})
        }
    }
}
</script>

<style scoped>

</style>
