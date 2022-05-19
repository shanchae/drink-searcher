<template>
    <div class="recipe">
        <div class="img-container">

        <img :src="recipe.strDrinkThumb" alt="">
        </div>
        <p class="drink-name">
            {{recipe.strDrink}}
        </p>
    </div>
</template>

<script setup>

    const props = defineProps({
        recipe: Object
    })

</script>