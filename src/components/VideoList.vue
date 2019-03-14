<template>
    <ul class="list-group col-md-4">
       <VideoListItem 
        v-for="video in videoList"
        :singleVideo="video"
        :key="video.etag"
        @videoSelect="onVideoSelected"
        >
       </VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem'
export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: {
        videoList: Array
    },
    methods: {
        onVideoSelected(video) {
            this.$emit('videoSelected', video)
        }
    }
}
</script>

<style>

</style>
