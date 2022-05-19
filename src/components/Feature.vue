<template>
    <div class="feature" @click="onClick">
        <img :src="recipe.strDrinkThumb" alt="">
        <div class="drink-name">
            {{recipe.strDrink}}
        </div>
    </div>
</template>
<script setup>

    const props = defineProps({
        recipe: Object
    })

    const emits = defineEmits(['recipe-details'])

    const onClick = () => {
        emits('recipe-details', props.recipe.idDrink)
    }
</script>