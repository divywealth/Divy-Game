<template>
    <div id="block" v-if="showBlock" @click="stopTimer">
        CLick Me
    </div>
</template>

<script>
export default {
    name: 'FirstChild',
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
        
        }
    },
    
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            this.showBlock = false
            clearInterval(this.timer)
            this.$emit('remove', this.reactionTime)
        }

    },
    
}
</script>

<style scoped>
#block{
    background: #0faf87 ;
    width: 400px;
    border-radius: 20px;
    color: white;
    padding: 100px 0;
    margin: 40px auto;
}
@media only screen and (max-width: 1000px) {
    #block{
        background: #0faf87 ;
        width: 300px;
        border-radius: 10px;
        color: white;
        padding: 100px 0;
        margin: 40px auto;
    }
}

</style>