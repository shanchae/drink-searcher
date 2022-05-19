<script setup>
  import { onMounted, ref } from 'vue'
  import Header from './components/Header.vue'
  import Features from './components/Features.vue'
  import RecipeList from './components/RecipeList.vue'
  import RecipeDetails from './components/RecipeDetails.vue'
  import axios from 'axios'

  const random = ref('')
  const features = ref([])
  const recipes = ref([])
  const displayFeature = ref(true)
  const recipeDetail = ref({})
  const isOpen = ref(false)

  onMounted(() => {
    axios.get(`https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${random.value}`)
        .then((resp) => {features.value = resp.data.drinks})
  })

  const search = (searchValue) => {
    axios.get(`https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${searchValue.value}`)
        .then((resp) => {
          recipes.value = resp.data.drinks
          displayFeature.value = false
        })
  }

  const selectCategory = (category) => {
    axios.get(`https://www.thecocktaildb.com/api/json/v1/1/filter.php?a=${category.value}`)
    .then((resp) => {
      recipes.value = resp.data.drinks
    })
      displayFeature.value = false
  }

  const selectFilter = (filter) => {
    axios.get(`https://www.thecocktaildb.com/api/json/v1/1/filter.php?c=${filter.value}`)
    .then((resp) => {
      recipes.value = resp.data.drinks
    })
      displayFeature.value = false
  }

  const showRecipe = (id) => {
    axios.get(`https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=${id}`)
    .then((resp) => {
      recipeDetail.value = resp.data.drinks[0]
      console.log(recipeDetail.value)
    })
    isOpen.value = true
  }

  const closeModal = () => {
    isOpen.value = false
  }

</script>

<template>
  <Header
    @search="search"
    @select-category="selectCategory"
    @click-filter="selectFilter"
  />
  <div v-show="displayFeature">
    <Features
      :recipes="features"
      @recipe-details="showRecipe"
    />
  </div>
  <RecipeList
    :recipes="recipes"
  />
  <RecipeDetails
    :isOpen="isOpen"
    :recipe="recipeDetail"
    @close-modal="closeModal"
  />
</template>


