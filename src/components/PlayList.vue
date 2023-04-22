<template>
    <div>
        <now-playing :playing_song="playing_song"></now-playing>
        <div v-if="new_play_list.length >= 1">
            <h2>Play List</h2>
            <article v-for="(song, i) in new_play_list" :key="i" @click="play_song" :title="song.title" :artist="song.artist" :image_url="song.image_url" :song_id="song.song_id">
                <img :src="song.image_url" :alt="song.title">
                <h3>{{song.title}} by {{song.artist}}</h3>
             </article>
        </div>
        <div v-else>
            <h2>Select a song from the list</h2>
        </div>
    </div>

</template>

<script>
import NowPlaying from '@/components/NowPlaying.vue'
    export default {
        methods: {
            play_song: function(event) {
                //If a song is already playing, push it back to the new_play_list before updating it to clicked song
                if(this.playing_song !== undefined) {
                    this.new_play_list.push(this.playing_song);
                } 
                this.playing_song = {
                    title: event.currentTarget.getAttribute(`title`),
                    artist: event.currentTarget.getAttribute(`artist`),
                    image_url: event.currentTarget.getAttribute(`image_url`),
                    song_id: event.currentTarget.getAttribute(`song_id`),
                }
                //Find the index of the song that was clicked to remove it from the playlist_array
                let index = this.new_play_list.findIndex((object) => { 
                    //this took me forever, but I finally catched on the fact that my attribute would return a string and so I should use == instead of ===
                    return object.song_id == event.currentTarget.getAttribute(`song_id`)});
                //Remove the object from the array at the index determined above.
                this.new_play_list.splice(index, 1);

            }
        },
        data() {
            return {
                playing_song: undefined,
                new_play_list: this.play_list
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