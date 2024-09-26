
<script setup>
import router from '@/router'

let newVotes = ''
let newImage = ''
let newTitle = ''
let newAuthor = ''
let newSubreddit = ''

function newPost() {
    console.log(typeof newVotes)
    let redditInformation = {
        "votes" : newVotes,
        "image" : newImage,
        "title" : newTitle,
        "author" : newAuthor,
        "subreddit" : newSubreddit
    }
    const params = {
        method: "POST",
        headers: {
            Accept: "application/json",
            "Content-Type": "application/json"
        },
        body: JSON.stringify(redditInformation),
    };
    fetch("http://localhost:3000/addpost", params)
    .then(response => response.json())
    .then(() => {
        router.push('/')
    })
}


</script>



<template>


<h2 class="newHeader"> Add New Post</h2>

<div class="addNew">
<p>Votes</p>
<input type="number" v-model="newVotes">
<p>Image Link</p>
<input type="text" v-model="newImage">
<p>Title</p>
<input type="text" v-model="newTitle">
<p>Author</p>
<input type="text" v-model="newAuthor">
<p>Subreddit</p>
<input type="text" v-model="newSubreddit">
</div>


<div class="submit">
    <button @click="newPost">Submit</button>
</div>

</template>



<style scoped>



.newHeader{
    font-weight: bold;
    text-align: center;
    
}

.addNew{
    text-align: center;
}


.submit{
    text-align: center;
    margin: 20px;
}

</style>























