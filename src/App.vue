<template>
  <v-app id="inspire">
    <v-app-bar
      app
      @click="drawer = !drawer"
      color="teal-darken-4"
      image="https://picsum.photos/1920/1080?random"
    >
      <template v-slot:image>
        <v-img
          gradient="to top right, rgba(19,84,122,.8), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <template v-slot:prepend>
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
      </template>

      <v-app-bar-title>My To-do-List</v-app-bar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <MyComponent />
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from "vue";
import MyComponent from "./components/MyComponent.vue";

const drawer = ref(null);
</script>

<script>
export default {
  data: () => ({ drawer: null }),
  components: {
    MyComponent,
  },
};
</script>