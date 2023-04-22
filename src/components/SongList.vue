<template>
    <div>
        <play-list :play_list="play_list"></play-list>
        <h2>Song List</h2>
        <section>
            <article v-for="(song, i) in songs" :key="i" @click="select_song" :title="song.title" :artist="song.artist" :image_url="song.image_url">
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
                //Create an auto incrementing ID so that each song duplicate has a unique identifier
                this.incrementing_id = this.incrementing_id + 1;
                let clicked_song = {
                        title: event.currentTarget.getAttribute(`title`),
                        artist: event.currentTarget.getAttribute(`artist`),
                        song_id: this.incrementing_id,
                        image_url: event.currentTarget.getAttribute(`image_url`)
                    };
                    //Push the clicked song object into the array
                    this.play_list.push(clicked_song);
                 },
             },
        data() {
            return {
                play_list: [],
                incrementing_id: 0,
                songs: [
                    {
                        title: `Teenage Drug`,
                        artist: `Ethan Gruska`,
                        image_url: `https://images.unsplash.com/photo-1509114397022-ed747cca3f65?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1635&q=80`
                    },
                    {
                        title: `Nicole`,
                        artist: `Taylor Ashton`,
                        image_url: `https://images.unsplash.com/photo-1500099817043-86d46000d58f?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1587&q=80`
                    },
                    {
                        title: `Causeway Road`,
                        artist: `Adam Baldwin`,
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