<template>
  <PageComponent title="Dashboard">
    <div v-if="loading" class="flex justify-center">Loading...</div>
    <div
      v-else
      class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5 text-gray-700"
    >
      <DashboardCard class="order-1 lg:order-2" style="animation-delay: 0.1s">
        <template v-slot:title>My Account</template>
        <div
          class="text-8xl pb-4 font-semibold flex-1 flex items-center justify-center"
        >
          <div
            class="max-w-xs bg-gray-800 rounded-full flex items-center text-sm focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white"
          >
            <span class="sr-only">Open user menu</span>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-24 w-24"
              fill="none"
              viewBox="0 0 24 24"
              stroke="white"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M5.121 17.804A13.937 13.937 0 0112 16c2.5 0 4.847.655 6.879 1.804M15 10a3 3 0 11-6 0 3 3 0 016 0zm6 2a9 9 0 11-18 0 9 9 0 0118 0z"
              />
            </svg>
          </div>
        </div>
      </DashboardCard>
      <DashboardCard class="order-2 lg:order-4" style="animation-delay: 0.2s">
        <template v-slot:title>Profile Pic</template>
        <div
          class="text-8xl pb-4 font-semibold flex-1 flex items-center justify-center"
        >
        </div>
      </DashboardCard>
      <DashboardCard
        class="order-3 lg:order-1 row-span-2"
        style="animation-delay: 0.2s"
      >
        <template v-slot:title>Library</template>
      </DashboardCard>
      <DashboardCard class="order-4 lg:order-3 row-span-2" style="animation-delay: 0.3s">
        <template v-slot:title>Decks</template>
      </DashboardCard>
    </div>
  </PageComponent>
</template>

<script setup>
import DashboardCard from "../components/core/DashboardCard.vue";
import PageComponent from "../components/PageComponent.vue";
import { computed } from "vue";
import { useStore } from "vuex";
import {
  MenuButton,
} from "@headlessui/vue";

const store = useStore();

const loading = computed(() => store.state.dashboard.loading);
const data = computed(() => store.state.dashboard.data);

store.dispatch("getDashboardData");
</script>

<style scoped></style>
