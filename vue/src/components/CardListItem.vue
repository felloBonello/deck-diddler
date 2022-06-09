<template>
  <div
    class="flex flex-col py-4 px-6 shadow-md bg-white hover:bg-gray-50 h-[470px]"
  >
    <img
      :src="
        card.image_url ||
        'https://st3.depositphotos.com/23594922/31822/v/600/depositphotos_318221368-stock-illustration-missing-picture-page-for-website.jpg'
      "
      :alt="card.name"
      class="w-full h-48 object-cover"
    />
    <h4 class="mt-4 text-lg font-bold">{{ card.name }}</h4>
    <div v-html="card.description" class="overflow-hidden flex-1"></div>
    <div v-html="card.flavour_text" class="overflow-hidden flex-1"></div>
  </div>
</template>

<script setup>

const { card } = defineProps({
  card: Object,
});
</script>

<style></style>
