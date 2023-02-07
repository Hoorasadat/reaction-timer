<template>
    <div class="block" v-if="showBlock" @click.self="calcTime">
        <h1>Click here to get your score</h1>
    </div>

</template>

<script>
export default {
    name: 'Block',
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            startTime: null,
            endTime: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true;
            this.startTime = Date.now();
            }, this.delay
        )
    },
    methods: {
        calcTime() {
            this.endTime = Date.now();
            this.reactionTime = this.endTime - this.startTime;
            this.showBlock = false;
            this.$emit('end', this.reactionTime)
        }
    }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.block{
    width: 500px;
    background-color: green;
    font-size: medium;
    color: azure;
    border-radius: 20px;
    border: 5px solid rgb(80, 78, 78);
    padding: 100px 0;
    margin: 40px auto;

}
h1 {
    padding-top: 10px;
}
</style>
