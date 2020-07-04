<template>
  <v-container>
    <v-row wrap>
      <v-col class="primary" cols="12" xs="12">
        <h1>12</h1>
      </v-col>
      <v-col class="success" cols="6" xs="6">
        <h1>6</h1>
      </v-col>
      <v-col class="error" cols="6" xs="6">
        <h1>6</h1>
      </v-col>
    </v-row>

    <v-row class="mt-5 justify-center align-center secondary" style="height:300px">
      <v-col class="blue lighten-1 orange--text text-center" cols="3" xs="3">
        <h1>Centrado</h1>
      </v-col>
      <v-col class="red white--text text-right" cols="3" xs="3">
        <h1>Derecha</h1>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <h1 class="display-1 text-uppercase">Lorem ipsum dolor</h1>
        <h1 class="display-2 primary pa-5 mt-5">Lorem ipsum dolor</h1>
        <h1 class="display-3 text-sm-center">Lorem ipsum dolor</h1>
        <h1 class="display-4">Lorem ipsum dolor</h1>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn>texto</v-btn>

        <v-btn color="primary">texto</v-btn>

        <v-btn color="red" dark>texto</v-btn>

        <v-btn color="blue" text>sin fondo</v-btn>

        <v-btn color="warning" large>Largo</v-btn>

        <v-btn color="warning" small>Largo</v-btn>

        <v-btn color="warning" disabled>Largo</v-btn>

        <v-btn color="red" depressed>texto</v-btn>

        <v-btn>
          <v-icon>forum</v-icon>
        </v-btn>
        <v-btn color="primary" icon flat>
          <v-icon>forum</v-icon>
        </v-btn>

        <v-btn color="primary" fab small>
          <v-icon>forum</v-icon>
        </v-btn>
        <v-btn color="primary" fab>
          <v-icon>forum</v-icon>
        </v-btn>
        <v-btn color="primary" fab large>
          <v-icon>forum</v-icon>
        </v-btn>

        <v-btn color="primary">
          texto
          <v-icon>forum</v-icon>
        </v-btn>
        <v-btn color="primary">
          texto
          <v-icon class="ml-2">forum</v-icon>
        </v-btn>
        <v-btn color="primary">
          texto
          <v-icon right>forum</v-icon>
        </v-btn>

        <v-btn color="primary">
          <v-icon left>forum</v-icon>
          texto
        </v-btn>

        <v-btn color="primary" outlined>
          <v-icon left>forum</v-icon>
          texto
        </v-btn>

        <v-btn color="primary" outlined block>
          <v-icon left>forum</v-icon>
          texto
        </v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  components: {},
};
</script>
