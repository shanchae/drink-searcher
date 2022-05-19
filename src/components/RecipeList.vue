<template>
    <div class="recipes">
        <div v-for="recipe in recipes" :key="recipe.id">
            <Recipe
                :recipe="recipe"
            />
        </div>
    </div>
</template>

<script setup>
    import Recipe from './Recipe.vue'

    const props = defineProps({
        recipes: Array
    })

</script>

