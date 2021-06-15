<template>
  <div class="s-tab">
    <div class="s-tab__content" v-show="title === selectedTitle">
      <slot />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, inject } from 'vue';
export default defineComponent({
  name: "STab",
  props: {
    title: {
      type: String,
    }
  },

  setup() {
    const selectedTitle = inject("selectedTitle");
    return {
      selectedTitle
    }
  }
});
</script>

<style scoped>
.s-tab {
  /*BLOCK*/
}

.s-tab__content {
  padding: 2rem;
}


</style>