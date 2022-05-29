<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row class="text-center">
          <v-col cols="12">
            <v-img
              :src="require('./assets/logo.png')"
              class="my-3"
              contain
              height="200"
            />
          </v-col>

          <v-col class="mb-4">
            <h1 class="display-2 font-weight-bold mb-3">Brazil Layoffs</h1>

            <p class="subheading font-weight-regular">
              Stats of Brazilian tech-startup layoffs
            </p>
          </v-col>

          <v-col class="mb-5" cols="12">
            <v-table fixed-header height="400px">
              <thead>
                <tr>
                  <th class="text-left">Company</th>
                  <th class="text-left">Layoffs</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in layoffs" :key="item.company">
                  <td>{{ item.company }}</td>
                  <td>{{ item.layoffs }}</td>
                </tr>
              </tbody>
            </v-table>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      layoffs: [],
    };
  },

  created() {
    fetch("./data.json")
      .then((response) => response.json())
      .then((data) => {
        this.layoffs = data;
      });
  },
};
</script>
