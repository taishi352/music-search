<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3 mt-5">
          音楽検索
        </h1>
        <br>
        <v-text-field
          v-model="keyword"
          :counter="100"
          label="アーティスト名を入力してください"
          required
        ></v-text-field>
        <br>
        <v-btn 
        color="primary"
        @click="search"
        >検索</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data(){
    return {
      keyword: '',
    }
  },
  methods:{
    search(){
      this.$router.push(`/result/${this.keyword}`)
    }
  }
}
</script>
