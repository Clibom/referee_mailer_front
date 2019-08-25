<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>GENERATEUR DE MAIL D'INDEMNITE D'ARBITRAGE DE RENCONTRE NATIONALE</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
    </v-app-bar>

    <v-content>
      <Form/>
    </v-content>
  </v-app>
</template>

<script>
import Form from './components/Form';

export default {
  name: 'App',
  components: {
    Form,
  },
  data: () => ({
    //
  }),
};
</script>
