<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <h1>転職体験談一覧（1156件）</h1>
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
}
export default Vue.extend({
  data(): DataType {
    return {
      dialog: false
    }
  },
  methods: {
    openModal():any{
      alert("OK")
    }
  }
})
</script>
