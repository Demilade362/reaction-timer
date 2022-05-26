<template>
    <p>Reaction Time - {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: [ "score" ],
    data(){
        return {
            rank: null,
        }
    },

    mounted() {
        if(this.score < 200){
            this.rank = 'Ninja Fingers'
        } else if(this.score < 400){
            this.rank = 'Rapid Reflexes'
        }else{
            this.rank = 'Snail Pace'
        }
    }

}
</script>

<style scoped>
    .rank{
        font-size: 1.4rem;
        color: crimson;
        font-weight: bold;
    }
</style>