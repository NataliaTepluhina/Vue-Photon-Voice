<template>
    <v-app id="inspire">
        <v-toolbar color="blue darken-4" dark fixed app>
          <img class="logo" src="./assets/logo.png" alt="Logo">
            <v-toolbar-title class="hidden-xs-only">Vue Photon Voice</v-toolbar-title>
            <v-spacer></v-spacer>
        </v-toolbar>
        <v-content class="blue lighten-3 lighten-3">
            <v-container class="app-container white" fill-height>
                <v-layout>
                  <v-flex xs12>
                        <v-btn fab dark color="blue darken-4">
                          <v-icon dark>mic</v-icon>
                        </v-btn>
                  </v-flex>
                </v-layout>
            </v-container>
        </v-content>
        <v-footer color="blue darken-4" app>
            <span class="footer-text text-xs-center white--text">Natalia Tepluhina &copy; 2018 </span>
        </v-footer>
    </v-app>
</template>

<script>
export default {
  name: 'app'
};
</script>

<style>
.logo {
  max-height: 100%;
}

.footer-text {
  width: 100%;
}
</style>
