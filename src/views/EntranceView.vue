<template>
  <div class="container">
    <v-sheet>
      <v-text-field label="ユーザ名" variant="outlined" placeholder="username" clearable></v-text-field>
    </v-sheet>
    <v-sheet>
      <v-text-field label="パスワード" variant="outlined" placeholder="password" clearable></v-text-field>
    </v-sheet>
    <v-btn block color="primary" variant="flat" class="ma-2" to="/home">ログインする</v-btn>
  </div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'EntranceView',
});
</script>
