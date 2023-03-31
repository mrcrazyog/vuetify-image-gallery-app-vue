<template>
  <v-card class="mx-5 my-2 pa-3">
    <v-row>
      <v-col v-for="n in 200" cols="4" sm="3" md="2" lg="1">
        <v-card
          @click="
            copyUrl(
              `https://picsum.photos/500/300?image=${n * 5 + 10}${
                isWithColor ? '' : '&grayscale'
              }`
            )
          "
        >
          <v-img
            :src="`https://picsum.photos/500/300?image=${n * 5 + 10}${
              isWithColor ? '' : '&grayscale'
            }`"
            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}${
              isWithColor ? '' : '&grayscale'
            }`"
            aspect-ratio="1"
            cover
            class="bg-grey-lighten-2"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  color="primary"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
        </v-card>
      </v-col>
    </v-row>
    <v-snackbar v-model="snackbarVisible" bottom right>
      URL copied to clipboard successfully
      <v-btn color="primary" text @click="snackbarVisible = false">
        Close
      </v-btn>
    </v-snackbar>
  </v-card>
</template>

<script setup>
import { ref } from 'vue';
const props = defineProps({
  isWithColor: {
    type: Boolean,
    default: true,
  },
});

const snackbarVisible = ref(false);

const copyUrl = async (url) => {
  await navigator.clipboard.writeText(url);
  snackbarVisible.value = true;
  setTimeout(() => (snackbarVisible.value = false), 2000);
};
</script>
