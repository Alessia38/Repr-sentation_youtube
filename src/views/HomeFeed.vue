<template>
    <div class="sm:px-32 flex flex-wrap justify-center">
        <VideoCard v-for="video in videos" :key="video.id" :videoInfo="video" />
    </div>
</template>

<script>
import VideoCard from "../components/VideoCard.vue";

export default {
    name: "HomeFeed",
    components: {
        VideoCard,
    },
    data() {
        return {
            videos: [],
        };
    },
    mounted() {
        const url = 
        "https://youtube138.p.rapidapi.com/channel/videos/?id=UCWeg2Pkate69NFdBeuRFTAw&filter=videos_latest";
        const options = {
            method: 'GET',
            headers: {
                'X-RapidAPI-Key': 'be22040c85msh54fe375e23305d0p1e6707jsn2fb55b75a50d',
                'X-RapidAPI-Host': 'youtube138.p.rapidapi.com'
            },
        };

        fetch(url, options)
        .then(response => response.json())
        .then(data => this.videos = data.contents)
        .catch((error) => console.error("Problem fetching the videos", error));
    },
};
</script>
