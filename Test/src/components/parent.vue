<template>
    <div id="Main">
        <h1>Divy Speed Test</h1>
        <button @click="Play" :disabled = isPlaying id="play">Play</button>
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
#play {
    border-radius: 10px;
    padding: 5px 30px;
    border: 1px solid #0faf87;
    font-weight: bold;
    font-size: 15px
}
#play:hover {
    color: white;
    background: #0faf87
}
#Main h1 {
    font-size: 50px
}
#Main button {
     margin-bottom: 30px
}
@media only screen and (max-width: 1000px) {
    #play {
        padding: 10px 35px;
        font-weight: bold;
        font-size: 20px
    }
    #Main{
    text-align: center;
    margin-top: 60%;
    
    }
    #Main h1 {
        font-size: 50px
    }
    #Main button {
        margin-bottom: 30px
    }
    
}
</style>
