<template>
    <h1 v-if="movieDetails">Movie Info</h1>
<div v-for="(item, index) in movieDetails" v-bind:key="index">
    <img v-bind:src="item.Poster" alt="">
    <div>
        Title: {{item.Title}}
    </div>
    <hr>
    <div>
        Year: {{item.Year}}
    </div>
    
</div>
</template>

<script>
export default {
    name: 'movieList',
    props:{
        movieDetails: Array
    }
}
</script>