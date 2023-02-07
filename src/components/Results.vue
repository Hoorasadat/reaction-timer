<template>
  <h2>Your score is {{ score }}ms</h2>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  name: 'Result',
  props: ['score'],
  data() {
      return {
        rank: null
      }
  },
  mounted() {
    if(this.score < 250) {
      this.rank = 'Ninja finger';
    } else if(this.score < 450) {
      this.rank = 'Rapid reflexes';
    } else {
      this.rank = 'snail pace...'
    }
  },
  methods: {

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
.rank{
  font-size: 1.4em;
  font-weight: bold;
  color: rgb(22, 142, 124);
}
</style>
