<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <h2>キャリア選択体験談一覧（1156件）</h2>
      <v-dialog
        v-model="dialog"
        width="500"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-chip
          class="ma-2"
          color="#0171BB"
          outlined
          v-bind="attrs"
          v-on="on"
        >
            <v-icon left color="#0171BB">
              mdi-filter
            </v-icon>
            絞り込む
          </v-chip>
        </template>
        <v-card>
          <FilterMenu section=Before />
          <FilterMenu section=After />
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              color="primary"
              text
              @click="dialog = false"
            >
              この条件で絞り込み
            </v-btn>
            <v-spacer></v-spacer>
          </v-card-actions>
        </v-card>
      </v-dialog>    
      <CareerPathCard :is-detail=false />
    </v-col>
  </v-row>
</template>


<script lang="ts">
import Vue from 'vue'

export type DataType = {
  dialog: boolean
  filter1:String
}
export default Vue.extend({
  data(): DataType {
    return {
      dialog: false,
      filter1:"before"
    }
  },
})
</script>
