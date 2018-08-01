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
                        <v-btn fab dark color="blue darken-4" @click="speechToText">
                          <v-icon dark>mic</v-icon>
                        </v-btn>
                        <h2 class="title">Result: {{result}}</h2>
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
import axios from 'axios';
export default {
  name: 'app',
  data() {
    return {
      recognition: null,
      result: '',
      colors: [
        'red',
        'magenta',
        'blue',
        'white',
        'orange',
        'green',
        'yellow',
        'cyan',
        'rainbow',
        'blink',
        'stop'
      ],
      activeColor: '',
      url:
        'https://api.particle.io/v1/devices/370027000947363339343638/colorMode?access_token=ee84182b5d73f2c4273aec9bc51f63e6d46b496f'
    };
  },
  methods: {
    speechToText() {
      this.recognition.start();
      this.recognition.onresult = event => {
        this.result = event.results[0][0].transcript.toLowerCase();
        const color = this.colors.find(
          item => this.result.indexOf(item) !== -1
        );
        if (color) {
          this.activeColor = color;
          axios.post(this.url, {
            color
          });
        }
      };
    }
  },
  mounted() {
    const SpeechRecognition =
      window.SpeechRecognition || window.webkitSpeechRecognition;
    if (!SpeechRecognition && process.env.NODE_ENV !== 'production') {
      throw new Error(
        'Speech Recognition does not exist on this browser. Use Chrome or Firefox'
      );
    }
    this.recognition = new SpeechRecognition();
    this.recognition.lang = 'en-US';

    this.recognition.onspeechend = () => {
      this.recognition.stop();
    };
  }
};
</script>

<style>
.logo {
  max-height: 100%;
}

.footer-text {
  width: 100%;
}

.title {
  padding-top: 20px;
}

.color-block {
  width: 200px;
  height: 200px;
  margin-top: 20px;
}
</style>
