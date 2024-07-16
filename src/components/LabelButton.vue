<!-- LabelButton.vue -->
<template>
  <v-btn color="#252525" dark class="label-btn" style="box-shadow: none">
    <span class="white--text label-text">{{ buttonText }}</span>
  </v-btn>
</template>

<script>
export default {
  name: "LabelButton",
  props: {
    buttonText: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
/* Add scoped styles here */
.label-btn {
  height: 32px;
}
.label-text {
  font-size: 11px;
}
</style>
