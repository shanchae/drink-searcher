<template>
    <div class="header">
        <div class="top">
            <h3 @click="home">Cocktail Recipe Searcher</h3>
            <div class="search">
                <input @change="handleSearch" type="search" name="" id="" placeholder="Search">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M500.3 443.7l-119.7-119.7c27.22-40.41 40.65-90.9 33.46-144.7C401.8 87.79 326.8 13.32 235.2 1.723C99.01-15.51-15.51 99.01 1.724 235.2c11.6 91.64 86.08 166.7 177.6 178.9c53.8 7.189 104.3-6.236 144.7-33.46l119.7 119.7c15.62 15.62 40.95 15.62 56.57 0C515.9 484.7 515.9 459.3 500.3 443.7zM79.1 208c0-70.58 57.42-128 128-128s128 57.42 128 128c0 70.58-57.42 128-128 128S79.1 278.6 79.1 208z"/></svg>
            </div>
        </div>
        <nav class="navigation">
            <ul>
                <li @click="clickCategory" id="Alcoholic">ALCOHOLIC</li>
                <li @click="clickCategory" id="Non_Alcoholic">NON-ALCOHOLIC</li>
                <li @click="clickFilter" id="Ordinary_Drink">ORDINARY DRINK</li>
                <li @click="clickFilter" id="Cocktail">COCKTAIL</li>
            </ul>
        </nav>
    </div>
</template>

<script setup>
    import { ref } from 'vue'

    const emits = defineEmits(['search', 'select-category', 'click-filter'])

    const searchValue = ref('')
    const category = ref('')
    const filter = ref('')

    const handleSearch = (e) => {
        e.preventDefault()

        searchValue.value = e.target.value

        emits('search', searchValue)
    }

    const clickCategory = (e) => {
        category.value = e.currentTarget.id

        emits('select-category', category)
    }

    const clickFilter = (e) => {
        filter.value = e.currentTarget.id

        emits('click-filter', filter)
    }

    const home = () => {
        window.location.reload()
    }

</script>