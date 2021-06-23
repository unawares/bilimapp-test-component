<template>
  <v-app id="app" class="noselect" light>
    <v-main>
      <nuxt />
    </v-main>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
    }
  }
}
</script>

<style lang="scss">
*, *:before, *:after {
  font-family: Roboto, "Helvetica Neue", Arial, sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
}

.noselect {
  -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
     -khtml-user-select: none; /* Konqueror HTML */
       -moz-user-select: none; /* Old versions of Firefox */
        -ms-user-select: none; /* Internet Explorer/Edge */
            user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome, Edge, Opera and Firefox */
}

.select {
  -webkit-touch-callout: text; /* iOS Safari */
    -webkit-user-select: text; /* Safari */
     -khtml-user-select: text; /* Konqueror HTML */
       -moz-user-select: text; /* Old versions of Firefox */
        -ms-user-select: text; /* Internet Explorer/Edge */
            user-select: text; /* Non-prefixed version, currently
                                  supported by Chrome, Edge, Opera and Firefox */
}

#app {
  background-color: var(--v-background-base);
}
</style>
