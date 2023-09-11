<template>
    <h1 class="text-lg mb-8">
        Posts
    </h1>
    <div class="mb-2">
        <Link :href="route('post.create')" class="hover:text-sky-500 hover:bg-white block p-2 w-32 bg-sky-500 border border-sky-500 rounded-full text-center text-white">Add Post</Link>
    </div>
    <div v-if="posts">
        <div class="mt-9 pt-8 border-t border-gray-300" v-for="post in posts">
            <div>id: {{ post.id}}</div>
            <div>title: {{ post.title}}</div>
            <div>content: {{ post.content}}</div>
            <div class="text-sm text-right">{{ post.date}}</div>
            <div class="text-sm text-right">
                <Link class="text-sky-500" :href="route('post.show', post.id)">Show</Link>
            </div>
            <div class="text-sm text-right">
                <Link class="text-sky-500" :href="route('post.edit', post.id)">Edit</Link>
            </div>
            <div class="text-sm text-right">
                <p @click.prevent="deletePost(post.id)" class="cursor-pointer text-red-500">Delete</p>
            </div>
        </div>

    </div>

</template>

<script>
import {Link} from "@inertiajs/vue3";
import MainLayout from "@/Layouts/MainLayout.vue";


export default {
    name: "Index",

    layout: MainLayout,

    props: [
        'posts'
    ],

    components: {
        Link
    },

    methods: {
        deletePost(id) {
            this.$inertia.delete(`/posts/${id}`)
        }
    }
}
</script>

<style scoped>

</style>
