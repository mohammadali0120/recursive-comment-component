<script setup lang="ts">
import "@fortawesome/fontawesome-free/js/all";

interface Props {
  icon: { prefix: string; value: string };
  classes?: string;
}
const props = defineProps<Props>();
</script>

<template>
  <div class="w-full h-full text-gray-600">
    <i
      class="block w-full h-full"
      :class="[icon.prefix, icon.value, classes]"
    ></i>
  </div>
</template>
