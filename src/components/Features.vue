<template>
    <div class="features"> 
        <div :key="recipe.id" v-for="recipe in recipes">
            <Feature
                :recipe="recipe"
                @recipe-details="onClickDrink"
            />
        </div>       
    </div>
</template>

<script setup>
    import Feature from './Feature.vue'

    const props = defineProps({
        recipes: Array
    })

    const emits = defineEmits(['recipe-details'])

    const onClickDrink = (id) => {
        emits('recipe-details', id)
    }
    
</script>