<template>
    <header>
        <div>
            <img :src="require('../assets/logo.png')" alt="">
        </div>
        <div class="search-bar">
            <input v-model="userSearchText" type="text">
            <!-- al click emit comunica ad app che la query è cambiata -->
            <button @click="$emit('searchDone', userSearchText)">Cerca</button> 
        </div>
    </header>  
</template>

<script>
export default {
    name: 'Header',
    data: function() {
        return {
            userSearchText: ''
        };
    }
}
</script>

<style lang="scss" scoped>
    header {
        background-color: black;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 20px;
    }
</style>