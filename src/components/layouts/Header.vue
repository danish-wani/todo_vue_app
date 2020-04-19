<template>
    <header>
        <h1>TodoList</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    /* header{
        display: flexbox;
        width: 400px; 
        margin-left: 35%;
        font-family: 'Courier New', Courier, monospace;
        font-size: large;
        text-align: center;
        align-self:center;
        flex: content;
        padding: 10px;
        background-color: #484444;
        color: white;
    } */
</style>