<template>
    <div>
        <p>Reaction Time: {{score}}ms</p>
        <h1>{{ rank }}</h1>
    </div>
</template>

<script>
export default {
    name: 'SecondChild',
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score < 250) {
            this.rank = 'Excellent'
        }else if(this.score < 400) {
            this.rank = 'Good'
        }else {
            this.rank = 'Poor'
        }
    }
    
}
</script>

<style scoped>



</style>