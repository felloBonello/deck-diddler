<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <PageComponent>
    <template v-slot:header>
      <div class="flex-grow justify-items-stretch">
        <h1 class="text-3xl font-bold text-gray-900">Search:</h1>
        <TInput
          name="search"
          v-model="state.search"
          :errors="errors"
          placeholder="Enter some stuff.."
          inputClass="rounded-t-md"
        />
      </div>
    </template>
    <div v-if="cards.loading" class="flex justify-center">Loading...</div>
    <div v-else-if="cards.data.length">
      <div class="grid grid-cols-1 gap-5 sm:grid-cols-2 md:grid-cols-3">
        <CardListItem
          v-for="(card, ind) in cards.data"
          :key="card.id"
          :card="card"
          class="opacity-0 animate-fade-in-down"
          :style="{ animationDelay: `${ind * 0.1}s` }"
        />
      </div>
      <div class="flex justify-center mt-5">
        <nav
          class="relative z-0 inline-flex justify-center rounded-md shadow-sm -space-x-px"
          aria-label="Pagination"
        >
          <!-- Current: "z-10 bg-indigo-50 border-indigo-500 text-indigo-600", Default: "bg-white border-gray-300 text-gray-500 hover:bg-gray-50" -->
          <a
            v-for="(link, i) of surveys.links"
            :key="i"
            :disabled="!link.url"
            href="#"
            @click="getForPage($event, link)"
            aria-current="page"
            class="relative inline-flex items-center px-4 py-2 border text-sm font-medium whitespace-nowrap"
            :class="[
              link.active
                ? 'z-10 bg-indigo-50 border-indigo-500 text-indigo-600'
                : 'bg-white border-gray-300 text-gray-500 hover:bg-gray-50',
              i === 0 ? 'rounded-l-md bg-gray-100 text-gray-700' : '',
              i === surveys.links.length - 1 ? 'rounded-r-md' : '',
            ]"
            v-html="link.label"
          >
          </a>
        </nav>
      </div>
    </div>
    <div v-else class="text-gray-600 text-center py-16">
      We couldn't find anything
    </div>
  </PageComponent>
</template>

<script setup>
import store from "../store";
import { computed } from "vue";
import TInput from '../components/core/TInput.vue'
import PageComponent from "../components/PageComponent.vue";
import CardListItem from "../components/CardListItem.vue";
import {ref} from "vue";

const cards = computed(() => store.state.cards);
const errors = ref({});
const state = {
  search: "",
};

</script>
