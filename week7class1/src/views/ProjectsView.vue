<template>
    <div :style="{fontSize: postFontSize + 'em'}">

<ol>
    <li v-for="data in datalist">{{ data.name }}</li>
</ol>

        This is projects page!
        <ProjectsComponent 
        v-for="post in posts"
        :title="post.title"
        :id="post.id"
        :key="post.id"
        
        @increase-size="increaseSize">

        Button name from Slot

        <template #footer>
This is new button with Named Slots
        </template>


        </ProjectsComponent>

        

        <!-- <ol>
            <li v-for="post in posts">{{ post.title }}</li>
        </ol> -->
    </div>

</template>

<script setup>

import { ref, onMounted } from 'vue'
import ProjectsComponent from '../components/ProjectsComponent.vue'

const posts = ref([])

const fetchposts = async () => {
    try {
        const response = await fetch("https://jsonplaceholder.typicode.com/posts")
        const data = await response.json()
        posts.value = data

    }
    catch (error) {
        console.error("Error fetching data...", error)
        
    }
}
onMounted(fetchposts)

const postFontSize = ref(1)

function increaseSize() {
    postFontSize.value += 1
}

import datafile from '../data/file.json'

const datalist = ref(datafile.rooms)

</script>

<style scoped>

</style>