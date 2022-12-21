<template>
  <v-app>
    <v-main>
        <todoList/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  components: {
    todoList,
  },

  data: () => ({
    //
  }),
};
</script>
