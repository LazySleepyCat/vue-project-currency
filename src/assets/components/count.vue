<script>
export default {
    props: {
        countRub: {
            type: Function
        }
    }
}
</script>

<template>
            <div class="main-block__count">
                <input type="number" class="main-block__count_value" placeholder="Введи число">                
                <!-- <input type="button"  @click="countRub()" class="main-block__count_button" value="Convert">                                -->
            </div>
          
</template>

<style scoped>

</style>
