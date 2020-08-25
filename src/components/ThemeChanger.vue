<template>
  <v-menu
    v-model="menu"
    :close-on-content-click="false"
    :nudge-width="200"
    offset-y
  >
    <template v-slot:activator="{ on }">
      <v-btn large icon dark v-on="on">
        <v-icon size="30" color="primary">mdi-palette</v-icon>
      </v-btn>
    </template>
    <v-card>
      <v-list-item>
        <v-list-item-content
          ><v-list-item-title class="font-weight-bold">
            Dark Mode</v-list-item-title
          >
        </v-list-item-content>
        <v-list-item-action
          ><v-switch v-model="$vuetify.theme.dark" />
        </v-list-item-action>
      </v-list-item>
      <v-divider />
      <v-card-text>
        <v-card class="my-2"
          :disabled="$vuetify.theme.themes.name === theme.name"
          @click="setTheme(theme)"
          hover
          outlined
          v-for="(theme, index) in themes"
          :key="index"
        >
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title class="font-weight-bold">
                {{ theme.name }}</v-list-item-title
              >
            </v-list-item-content>
            <v-list-item-action>
              <v-avatar
                color="success"
                size="30"
                v-if="$vuetify.theme.themes.name === theme.name"
              >
                <v-icon>mdi-check</v-icon>
              </v-avatar>
            </v-list-item-action>
          </v-list-item>
          <div class="my-2">
            <v-chip
              class="mx-1"
              label
              :color="theme.dark[key]"
              v-for="(key, index) in Object.keys(theme.dark)"
              :key="index"
            >
              {{ key }}</v-chip
            >
          </div>
          <div class="my-2">
            <v-chip
              class="mx-1"
              label
              :color="theme.light[key]"
              v-for="(key, index) in Object.keys(theme.light)"
              :key="index"
            >
              {{ key }}</v-chip
            >
          </div>
        </v-card>
      </v-card-text>
      <v-divider />
      <v-card-actions>
        <v-btn text @click="menu = false" color="grey">Close</v-btn>
        <v-spacer />
      </v-card-actions>
    </v-card> </v-menu
></template>

<script>
export default {
  name: "ThemeChanger",
  data: () => ({
    menu: false,
    themes: [
      {
        name: "Theme 1",
        dark: {
          primary: "#21CFF3",
          accent: "#FF4081",
          secondary: "#21dc79",
          success: "#86af3f",
          info: "#f34fc6",
          warning: "#FB8C00",
          error: "#FF5252"
        },
        light: {
          primary: "#22daff",
          accent: "#ff6b99",
          secondary: "#26ff8c",
          success: "#a5d64c",
          info: "#ff53d0",
          warning: "#ff8e00",
          error: "#ff5252"
        }
      },
      {
        name: "Theme 2",
        dark: {
          primary: "#E65100",
          accent: "#7CB342",
          secondary: "#689F38",
          success: "#4CAF50",
          info: "#6156d8",
          warning: "#1565C0",
          error: "#FF7043"
        },
        light: {
          primary: "#ffa450",
          accent: "#a1e754",
          secondary: "#92de4e",
          success: "#6dff74",
          info: "#7365ff",
          warning: "#2e8ac0",
          error: "#ff5e3c"
        }
      },
      {
        name: "Theme 3",
        dark: {
          primary: "#33691E",
          accent: "#FFCA28",
          secondary: "#607D8B",
          success: "#FFEB3B",
          info: "#2196F3",
          warning: "#9C27B0",
          error: "#B71C1C"
        },
        light: {
          primary: "#6ae240",
          accent: "#ffe063",
          secondary: "#7ea4b6",
          success: "#ffea70",
          info: "#229eff",
          warning: "#e239ff",
          error: "#e82424"
        }
      }
    ]
  }),
  methods: {
    setTheme(theme) {
      // close menu
      this.menu = false;
      const name = theme.name;
      const dark = theme.dark;
      const light = theme.light;
      // set themes
      Object.keys(dark).forEach(i => {
        this.$vuetify.theme.themes.dark[i] = dark[i];
      });
      Object.keys(light).forEach(i => {
        this.$vuetify.theme.themes.light[i] = light[i];
      });
      // also save theme name to disable selection
      this.$vuetify.theme.themes.name = name;
    }
  }
};
</script>
<style scoped></style>
