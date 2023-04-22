<template>
    <div>
        <h2>Now Playing</h2>
        <div>
            <img :src="playing_song.image_url" :alt="playing_song.title">
            <h3>{{playing_song.title}} by {{playing_song.artist}}</h3>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            playing_song: Object
        }
    }
</script>

<style scoped>
    img {
        width: 50px;
        height:50px;
        object-fit: cover;
    }
</style>