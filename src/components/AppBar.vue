<template>
  <v-app-bar app color="black" dark :height="44">
    <!-- Left Side: Current Time (Minute Only) -->
    <v-toolbar-title class="appbar-header">{{ currentMinute }}</v-toolbar-title>

    <!-- Right Side: Network Signal and Horizontal Battery Icon -->
    <v-spacer></v-spacer>
    <!-- Pushes the icons to the right -->
    <v-icon class="mr-2 appbar-icon">mdi-signal</v-icon>
    <v-icon class="mr-2 appbar-icon">mdi-wifi</v-icon>
    <v-icon class="mr-5 appbar-icon">mdi-battery</v-icon>

    <!-- Optionally, you can add additional icons or components here -->
  </v-app-bar>
</template>

<script>
export default {
  name: "AppBar",
  data() {
    return {
      currentMinute: new Date().toLocaleTimeString([], {
        hour: "2-digit",
        minute: "2-digit",
      }),
    };
  },
  mounted() {
    // Update current minute every minute (60 seconds)
    setInterval(() => {
      this.currentMinute = new Date().toLocaleTimeString([], {
        hour: "2-digit",
        minute: "2-digit",
      });
    }, 60000); // Update every 60 seconds
  },
};
</script>

<style>
.appbar-header {
  font-size: 14px;
  padding-left: 14px;
  margin-top: 1px;
}
.appbar-icon {
  font-size: 15px;
}
</style>
