<!-- GridLayout.vue -->
<template>
  <v-container>
    <!-- Center the Grid and Adjust Columns Responsively -->
    <v-row dense justify="center">
      <!-- Responsive Column Sizes -->
      <v-col v-for="(item, index) in items" :key="index" :cols="3">
        <LabelButton :buttonText="item" width="100%" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import LabelButton from "@/components/LabelButton.vue"; // Adjust the path as per your project structure

export default {
  components: {
    LabelButton,
  },
  data() {
    return {
      items: [
        "标题标题",
        "标题标题",
        "标题标题",
        "标题标题",
        "标题标题",
        "标题标题",
        "标题标题",
        "标题标题",
        "标题标题",
        "标题标题",
        "标题标题",
        "标题标题",
      ],
    };
  },
};
</script>

<style scoped>
/* Add scoped styles here */
</style>
