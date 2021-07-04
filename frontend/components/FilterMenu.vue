<template>
<div class="px-10 pt-5">
  <h3>{{section}}</h3>
  <v-combobox
    v-model="chips"
    :items="items"
    chips
    clearable
    :label=section
    multiple
    solo
  >
    <template v-slot:selection="{ attrs, item, select, selected }">
      <v-chip
        v-bind="attrs"
        :input-value="selected"
        close
        @click="select"
        @click:close="remove(item)"
        dark
        color="#0171BB"
      >
        <strong>{{ item }}</strong>&nbsp;
      </v-chip>
    </template>
  </v-combobox>
</div>
</template>

<script>
import Vue from 'vue'
export default Vue.extend({
    props:{
      section: {
        type: String,
        required: true,
      }
    },
    data () {
      return {
        chips: [],
        items: ['IT/通信','メーカー','人材/教育','コンサル','理学部','工学部','文学部','経済学部'],
      }
    },

    methods: {
      remove (item) {
        this.chips.splice(this.chips.indexOf(item), 1)
        this.chips = [...this.chips]
      },
    },
  })
</script>