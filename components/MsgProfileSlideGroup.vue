<script setup lang="ts">
  const props = defineProps({
    profiles: {
        type: [Object],
        required: false
    }
  })
</script>

<template>
    <v-sheet
      class="mx-auto"
      elevation="8"
      max-width="90%"
      height="100%"
    >
    <v-slide-group
      v-model="model"
      selected-class="bg-success"
      show-arrows
    >
      <v-slide-group-item
        v-for="profile in profiles"
        :key="profile"
        v-slot="{ isSelected, toggle, selectedClass }"
      >
      <MsgProfileContent :profile="profile"/>
      </v-slide-group-item>
    </v-slide-group>
  </v-sheet>
</template>
