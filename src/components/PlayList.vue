<template>
    <div>
        <now-playing :playing_song="playing_song"></now-playing>
        <div>
            <h2>Play List</h2>
            <article v-for="(song, i) in play_list" :key="i" @click="play_song" :title="song.title" :artist="song.artist" :image_url="song.image_url" :song_id="song.song_id">
                <img :src="song.image_url" :alt="song.title">
                <h3>{{song.title}} by {{song.artist}}</h3>
             </article>
        </div>
    </div>

</template>

<script>
import NowPlaying from '@/components/NowPlaying.vue'
    export default {
        methods: {
            play_song: function(event) {
                this.playing_song = {
                    title: event.currentTarget.getAttribute(`title`),
                    artist: event.currentTarget.getAttribute(`artist`),
                    image_url: event.currentTarget.getAttribute(`image_url`),
                    song_id: event.currentTarget.getAttribute(`song_id`)
                }
            }
        },
        data() {
            return {
                playing_song: undefined
            }
        },
        components: {
            NowPlaying
        },
        props: {
            play_list: Array,
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