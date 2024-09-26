<script setup>

//VUE APP appears in localhost:5173

//connect EXPRESS APP to VUE APP
import RedditFeed from '@/components/RedditFeed.vue'
import {reactive} from 'vue'

let redditPost = reactive([])


fetch("http://localhost:3000/reddit")
.then(response => {
return response.json()
})
.then(post => {
    redditPost.push(...post)
})
//connect EXPRESS APP to VUE APP

</script>



<template>

<!-- connect EXPRESS APP to VUE APP -->
<div>
<RedditFeed v-for="feed in redditPost" :redditInfo="feed"></RedditFeed>
</div>
<!-- connect EXPRESS APP to VUE APP -->



</template>




<style scoped>



</style>