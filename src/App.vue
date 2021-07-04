<template>
  <v-app>
    <v-main>
      <user-form/>
    </v-main>
  </v-app>
</template>

<script>
// import UserForm from './components/UserForm.vue';
import UserForm from './components/UserForm2.vue';

export default {
  name: 'App',

  components: {
    UserForm,
  },

  data: () => ({
    //
  }),
};
</script>
