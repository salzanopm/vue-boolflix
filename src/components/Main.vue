<template>
  <main>
     <ul>
         <li>ciao</li>
     </ul>
  </main>
</template>

<script>

export default {
    name:'Main',
    components: {
        Cards,
    }
}
</script>

<style scoped>
ul {
    display: flex;
    flex-wrap: wrap;

}
    li {
        list-style-type: none;
        width:calc(100% / 4);
    }

</style>