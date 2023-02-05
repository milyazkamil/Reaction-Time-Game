<template>
    <div class="red-box">
        <img class="gif" src="@/assets/gif.gif" alt="loading gif">
        <h2>Please Wait</h2>
    </div>
</template>

<script>
export default {
    name: "RedBox",
}
</script>

<style scoped>
.red-box {
    width: 300px;
    height: 300px;
    border-radius: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: rgb(255, 0, 0);
    margin: 0 auto;
    margin-top: 40px;
    cursor: pointer;
} 
.gif {
    width: 50px;
    height: 50px;
}
</style>