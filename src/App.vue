<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-items>
        <v-list-item dense>
          <v-list-item-avatar class="mx-0">
            <v-img
              :src="require('@/assets/logo.svg')"
              :width="30"
              :height="30"
              contain
            />
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title class="primary--text">
              <span class="font-weight-bold title">Dynamic</span>
              <span class="font-weight-light title"
                >Theme</span
              ></v-list-item-title
            >
          </v-list-item-content>
        </v-list-item>
      </v-toolbar-items>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <ThemeChanger />
      </v-toolbar-items>
    </v-app-bar>

    <v-main>
      <Dashboard />
    </v-main>
  </v-app>
</template>

<script>
import Dashboard from "./components/sample/Dashboard";
import ThemeChanger from "./components/ThemeChanger";
export default {
  name: "App",

  components: {
    Dashboard,
    ThemeChanger
  }
};
</script>
