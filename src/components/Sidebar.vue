<template>
  <v-navigation-drawer expand-on-hover rail permanent>
    <v-list>
      <v-list-item
        prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
        title="Jan Michalcak"
        subtitle="jan.michalcak@gmail.com"
        nav
      >
      </v-list-item>
    </v-list>
    <v-divider></v-divider>
    <v-list density="compact" nav>
      <v-list-item
        prepend-icon="mdi-image"
        title="Color gallery"
        value="color"
        @click="selectOption(true)"
      ></v-list-item>
      <v-list-item
        prepend-icon="mdi-menu"
        title="Grayscale gallery"
        value="color"
        @click="selectOption(false)"
      ></v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script setup>
const emits = defineEmits(['selectOption']);

const selectOption = (option) => {
  emits('selectOption', option);
};
</script>
