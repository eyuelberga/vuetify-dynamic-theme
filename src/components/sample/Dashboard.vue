<template>
  <v-container fluid>
    <v-row>
      <v-col cols="6">
        <Form/>
      </v-col>
      <v-col cols="6">
        <v-alert dense type="warning">
          Warning Alert
        </v-alert>
        <v-alert dense type="info">
          Info Alert
        </v-alert>
        <v-alert dense type="success">
          Success Alert
        </v-alert>
        <v-alert dense type="error">
          Error Alert
        </v-alert>
      </v-col>
      <v-col cols="6">

        <HeartRate />
      </v-col>
      <v-col cols="6">
        <Weather />
      </v-col>
    </v-row>
    <v-btn dark fab bottom fixed right color="secondary">
      <v-icon>mdi-plus</v-icon>
    </v-btn>
  </v-container>
</template>

<script>
import Weather from "./Weather";
import HeartRate from "./HeartRate";
import Form from "./Form";
export default {
  components: {
    Weather,
    HeartRate,
    Form
  },

  data: () => ({})
};
</script>
