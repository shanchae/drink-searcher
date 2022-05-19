<template>
    <div class="recipe-details" v-show="isOpen" @click.self="emits('close-modal')">
        <div class="modal">
            <div class="modal-content">
                <img :src="recipe.strDrinkThumb" alt="">
                <div class="recipe">
                    <h3>{{recipe.strDrink}}</h3>
                    Ingredients:
                    <div class="ingredients">
                        <ul>
                            <li>{{recipe.strMeasure1}}</li>
                            <li>{{recipe.strMeasure2}}</li>
                            <li>{{recipe.strMeasure3}}</li>
                        </ul>
                        <ul>
                            <li>{{recipe.strIngredient1}}</li>
                            <li>{{recipe.strIngredient2}}</li>
                            <li>{{recipe.strIngredient3}}</li>
                        </ul>
                    </div>
                    <div class="instructions">
                        Instructions:
                        <p>{{recipe.strInstructions}}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>

    const props = defineProps({
        recipe: Object,
        isOpen: Boolean
    })

    const emits = defineEmits('close-modal')
</script>