<script setup>
import { ref } from 'vue';
const menuselected = ref(0)
import DailyViewVue from '@/views/DailyView.vue'

</script>

<template>
  <v-layout class="rounded rounded-md">
    <v-app-bar title="Track expenses"></v-app-bar>

    <v-navigation-drawer>
      <v-list>
        <v-list-item @click="menuselected=0" title="Track expenses"></v-list-item>
        <v-list-item @click="menuselected=1" title="Future Transaction"></v-list-item>
        <v-list-item @click="menuselected=3" title="Recurring Transaction"></v-list-item>

      </v-list>
    </v-navigation-drawer>
    <v-main v-if="menuselected===0" >
      <DailyViewVue/>
    </v-main>

    <v-main v-if="menuselected===1">
      2
    </v-main>

    <v-main v-if="menuselected===3">
      3
    </v-main>
  </v-layout>

</template>

<style scoped>

</style>
