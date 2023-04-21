<template>
    <div>
        <play-list :play_list="play_list"></play-list>
        <h2>Song List</h2>
        <section>
            <article v-for="(song, i) in songs" :key="i" @click="select_song" :title="song.title" :artist="song.artist" :image_url="song.image_url" :song_id="song.song_id" >
                <img :src="song.image_url" :alt="song.title">
                <h4>{{song.title}} by {{song.artist}}</h4>
            </article>
        </section>
    </div>
</template>

<script>
import PlayList from '@/components/PlayList.vue'
    export default {
        components: {
            PlayList
        },
        methods: {
            select_song: function(event) {
                let clicked_song = {
                        title: event.currentTarget.getAttribute(`title`),
                        artist: event.currentTarget.getAttribute(`artist`),
                        song_id: event.currentTarget.getAttribute(`song_id`),
                        image_url: event.currentTarget.getAttribute(`image_url`)
                    };
                    this.play_list.push(clicked_song);
                 },
             },
        data() {
            return {
                play_list: [],
                songs: [
                    {
                        title: `Teenage Drug`,
                        artist: `Ethan Gruska`,
                        song_id: 1,
                        image_url: `https://images.unsplash.com/photo-1509114397022-ed747cca3f65?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1635&q=80`
                    },
                    {
                        title: `Nicole`,
                        artist: `Taylor Ashton`,
                        song_id: 2,
                        image_url: `https://images.unsplash.com/photo-1500099817043-86d46000d58f?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1587&q=80`
                    },
                    {
                        title: `Causeway Road`,
                        artist: `Adam Baldwin`,
                        song_id: 3,
                        image_url: `https://images.unsplash.com/photo-1487260211189-670c54da558d?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1587&q=80`
                    }   
                ]
            }
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