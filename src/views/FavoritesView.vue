<script setup>

import {useFavoritesStore} from '@/store/favorites';
import { storeToRefs } from 'pinia';
import {RouterLink} from 'vue-router';



const useFavorites = useFavoritesStore();

const {favorites} = storeToRefs(useFavorites);

const {remove} = useFavorites;

</script>



<template>

    <h1>Favoritos</h1>
    <p v-if="favorites.length === 0">Sin favoritos</p>
    <ul class="list-group" v-else>
        <li 
            class="list-group-item"
            v-for="poke in favorites"
            :key="poke.id"
        > 
            <div>
                {{ poke.name}}
            </div>

            <div>
                
                <router-link class="btn btn-sm btn-primary me-2" :to="`/pokemons/${poke.name}`">Mas información</router-link>

                <button class="btn btn-sm btn-danger" @click="remove(poke.id)">Eliminar</button>
            </div>
            
        </li>
    </ul>

</template>