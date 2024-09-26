<script setup>
// import {RouterView} from 'vue-router'
</script>




<template>

<img class="redditImage" src="../src/assets/redditLogo.png">
 
 <!-- //used W3 schools to create the nav bar -->
 <div class="topnav">
  <a class="active">hot</a>
  <a href="news">new</a>
  <a href="contact">rising</a>
  <a href="about">controversial</a>
  <a href="about">top</a>
  <a href="about">wiki</a>
  <RouterLink to="/add" class="newPost">Add New Post</RouterLink>


</div>



 <RouterView />



 <footer>
  <p>Creator: Haja of the Kamaras</p>
  <p><a href="hege@example.com">hugeburnafan@burnaboy.com</a></p>
</footer>
</template>



<style scoped>

.redditImage{
  width: 150px;
  margin-left: 20px;
  
}

.topnav {
  background-color: rgb(148, 202, 219);
  overflow: hidden;
  border-radius: 10px;
  margin-top: 10px;
}


.topnav a {
  float: left;
  color: darkblue;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
}

/* Change the color of links on hover */
.topnav a:hover {
  background-color: #ddd;
  color: black;
}

/* Add a color to the active/current link */
.topnav a.active {
  background-color: red;
  color: white;
}

.newPost{
  color: rgb(0, 174, 255);
  font-size: 20px;
  margin-left: 1300px;
  text-decoration: underline;
}

footer {
  text-align: center;
  padding: 3px;
  background-color: rgb(148, 202, 219);
  overflow: hidden;
  border-radius: 10px;;
  color: white;
  margin-top: 120px;
  width: 100%;
}

</style>



















