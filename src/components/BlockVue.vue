<template>
    <div class="box" @click="timer">
        <h1>Click Me</h1>
    </div>
</template>

<script>
export default {
    name: "BlockVue",
    data() {
        return {
            result: 0,
        }
    },
    props: ["delay"],
    mounted() {
        setInterval(() => {
            this.result += 10;
        }, 10);
         
    },
    methods: {
        timer() {
            this.$emit('stopTimer', this.result)
        }
    }  
}
</script>

<style scoped>
.box {
    width: 300px;
    height: 300px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: rgb(0, 255, 42);
    margin: 0 auto;
    margin-top: 40px ;
    cursor: pointer;
}
</style>