<template>
    <header>
        <input v-model="userSearchText" type="text">
        <!-- al click emit comunica ad app che la query è cambiata -->
        <button @click="$emit('searchDone', userSearchText)">Cerca</button> 
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