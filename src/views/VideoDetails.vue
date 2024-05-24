<template>
    <div class="px-8 flex flex-col items-center">
        <div class="video-container sm:w-2/3 w-4/5 relative">
            <iframe :src="`https://youtube.com/embed/${$route.params.id}`" class="video rounded-xl shadow-lg w-full h-full"></iframe>
        </div>
        <h3 class="mt-4 text-center text-lg">{{ videoInfo.title }}</h3>
    </div>
</template>

<script>
export default {
    name: "VideoDetails",
    data() {
        return {
            videoInfo: [],
        };
    },
    mounted() {
        const url = 'https://youtube138.p.rapidapi.com/video/details/?id=' + 
        this.$route.params.id;
        const options = {
            method: 'GET',
            headers: {
                'X-RapidAPI-Key': 'be22040c85msh54fe375e23305d0p1e6707jsn2fb55b75a50d',
                'X-RapidAPI-Host': 'youtube138.p.rapidapi.com'
            },
        };

        fetch(url, options)
            .then(response => response.json())
            .then(data => this.videoInfo = data)
            .catch(error => console.error("Error fetching video:", error));
    },
};
</script>

<style>
.video-container {
    padding-top: 40.25%; /* Ratio 16:9 */
    position: relative;
    margin: 0 auto 10px auto;
}

.video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
</style>
