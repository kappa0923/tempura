<template>
  <v-card outlined shaped>
    <v-card-title>
      {{ eventData.title }}
    </v-card-title>
    <v-card-subtitle>
      {{ eventData.date }}
    </v-card-subtitle>
    <v-card-text>
      {{ eventData.detail | truncate(100) }}
    </v-card-text>
    <v-card-actions>
      <a :href="eventData.link">See More</a>
      <!-- <v-btn outlined rounded text> Button </v-btn> -->
    </v-card-actions>
  </v-card>
</template>

<script lang="ts">
import { PropOptions } from 'vue'

export default {
  props: {
    eventData: {
      type: Object,
      required: true,
    } as PropOptions<Event>,
  },
}
</script>
