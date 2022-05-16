<template>
  <div class="grid grid-flow-col grid-cols-[288px] w-full">
    <SideBar />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import SideBar from "@/components/SideBar.vue";

export default Vue.extend({
  name: "App",
  components: {
    SideBar,
  },
});
</script>
