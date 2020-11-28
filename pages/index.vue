<template>
  <div class="container">
    <div>
      <Logo />
      <h2 class="subtitle"> {{ savoir }} </h2>
      <div class="links">
        <bouton @click="nouveauSavoir()" class="button--green">Nouveau savoir</bouton>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {

  data() {
    return {
      savoir: "Défaut",
      url: 'https://uselessfacts.jsph.pl/random.json?language=en'
    }
  },

  mounted() {
    axios.get(this.url).then(response => this.savoir = response.data.text)
  },

  methods: {
    nouveauSavoir() {
      axios.get(this.url).then(response => this.savoir = response.data.text)
    }
  }

}

</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
