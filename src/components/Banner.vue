<template>
    <div id="banner">
        <h1>Make Your Burger</h1>
    </div>

</template>

<script>


export default {
    name: 'Banner'
}

</script>

<style scoped>

    #banner {
        background-image: url('/public/img/burger.jpg');
        background-attachment: fixed;
        background-size: cover;
        height:500px;
        background-position: 0 -140px;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        margin-bottom: 24px;
    }

    h1{
        color: #222;
        padding: 18px;
        font-size: 42px;
        background: #fff;
        border-top-right-radius: 8px;
    }

</style>