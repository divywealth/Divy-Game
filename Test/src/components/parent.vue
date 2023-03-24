<template>
    <div id="Main">
        <h1>Ninja Reaction Timer</h1>
        <button @click="Play" :disabled = isPlaying>Play</button>
        <FirstChild :delay= "delay" 
        v-if="isPlaying"
        @remove= "remove"
        />
        <SecondChild v-if="isDonePlaying" :score = "score"/>
    </div>
</template>

<script>
import FirstChild from './ParentChild/FirstChild.vue';
import SecondChild from './ParentChild/SecondChild.vue';

export default {
    name: 'parent',
    components: {FirstChild, SecondChild},
    data() {
        return {
            isPlaying: false,
            delay: null,
            isDonePlaying: false,
            score: null
        }
    },
    methods: {
        Play(){
            this.isPlaying = true;
            this.delay = 2000 + Math.random( ) * 5000
            this.isDonePlaying = false
        },
        remove(passed) {
            this.isPlaying = false
            this.isDonePlaying = !this.isDonePlaying
            this.score = passed
        }
    }
   
    
}
</script>

<style scoped>
#Main{
    text-align: center;
    margin-top: 60px;
}

</style>
