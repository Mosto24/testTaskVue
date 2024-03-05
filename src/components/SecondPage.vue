<template>
    <div class="result">
       {{ data }} 
    </div>
</template>

<script>
    export default {
        props: ['json'],
        data() {
            return {
                data: this.json
            }
        }
    }
</script>

<style>

</style>