<template>
  <div>
    <NuxtRouteAnnouncer />
    <VueCanvas/>
  </div>
</template>

<script>
  import VueCanvas from "@/components/tgfx-001.vue";

  export default {
    components: {
      VueCanvas
    }
  };
</script>
