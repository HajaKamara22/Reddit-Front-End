
<script setup>

import { ref } from 'vue';

const props = defineProps(['redditInfo'])


const liked = ref(false);

function whenLiked(isUpvote) {
    const newVotes = isUpvote ? props.redditInfo.votes + 1 : props.redditInfo.votes - 1;

    fetch(`http://localhost:3000/reddit/${props.redditInfo.id}`, {
        method: 'PUT',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify({ votes: newVotes }),
    })
    .then(response => response.json())
    .then(updatedPost => {
        if (updatedPost) {
            props.redditInfo.votes = updatedPost.votes; // Update the votes in the UI
        }
    })
    .catch(error => {
        console.log('Error updating votes:', error);
    });
}

</script>



<template>




<div class="redditContainer">
    <div class="card-info">
        
        <div class="votes">
        <img  @click="whenLiked(true)" class="redarrows" src="../assets/newuparrow.jpeg" >
        <p >{{ redditInfo.votes }}</p>
        <img  @click="whenLiked(false)" class="arrows" src="../assets/new-new.png">
        </div>


        <div>
        <img class="image" :src="redditInfo.image">
        </div>


        <div class="dataInfo">
            <div class="title">
        <p>{{ redditInfo.title }}</p>
            </div>
        <div class="redditAuthor">
        <span class="">{{ redditInfo.author }}</span>
        <span> 40 comments </span>
        <span>save </span>
        <span>repost</span>
        <span> about</span>
        <span class="sub">{{ redditInfo.subreddit }}</span>

        </div>
        </div>
    </div>

</div>




</template>




<style scoped>

.redditContainer{
    margin-top: 70px;
    margin-left: 20px;
  
}
.image{
    width: 100px;
   
}

.card-info{
    display: flex;
  align-items: center;
  margin: 10px;
  margin-bottom: -70px;
 
}

.votes{
    padding: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
    
}

.dataInfo{
   padding: 10px;
   
}

.title{
    margin-top: -20px;
    color: blue;
    font-size: larger;
   
}


.redditAuthor{
    /* margin-top: 40px; */
    color: gray;
    font-size: small;
  
}

.sub{
    margin-left: 10px;
}

.redarrows{
    width: 60px;
    margin-right: -4px;
    
   
}

.arrows{
    width: 25px;
    margin-left: 4px;

}
</style>
























