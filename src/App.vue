<script setup>
let refresh = () => {
  window.location.reload();
}
</script>

<template>
  <v-app>
    <v-main>
      <v-app-bar :elevation="2">
      <template v-slot:append>
        <v-app-bar-nav-icon icon="mdi-refresh" @click="refresh"></v-app-bar-nav-icon>
      </template>
      <v-app-bar-title>AI Chat</v-app-bar-title>
      </v-app-bar>

      <router-view />

    </v-main>
  </v-app>
</template>
