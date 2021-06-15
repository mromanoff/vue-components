<template>
  <div class="s-tabs">
    <nav class="s-tabs__nav">
      <button v-for="title in tabTitles"
        :key="title"
        @click="selectedTitle = title"
        role="tab"
        class="s-tabs__button"
        :class="{
          's-tabs__button--active': title === selectedTitle,
          's-tabs__button--disabled': false
        }"
        :ariaSelected="String(title === selectedTitle)"
        :disabled="false"
      >
        {{title}}
      </button>
    </nav>
    <div class="s-tabs__content">
      <slot />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, provide } from 'vue';
export default defineComponent({
  name: "STabs",

  setup(props, { slots }) {
    const tabTitles = ref(slots.default().map(item => item.props.title));
    const selectedTitle = ref(tabTitles.value[0]);
    provide("selectedTitle", selectedTitle);
    return {
      selectedTitle,
      tabTitles
    }
  }
});
</script>

<style scoped>
.s-tabs {
  display: flex;
  flex-direction: column;
}

.s-tabs__nav {
  margin-bottom: 1rem;
  list-style: none;
  display: flex;
}

.s-tabs__button {
  font-size: small;
  font-weight: 700;
  padding: 1rem 2rem 0.75rem;
  display: inline-flex;
  align-items: center;
  text-decoration: none;
  border: none;
  background-color: transparent;
  border-bottom: 0.25rem solid transparent;
  cursor: pointer;
  transition: all 250ms;
}

.s-tabs__button--active {
  border-bottom: 0.25rem solid black;
}

.s-tabs__button--disabled {
  opacity: 0.5;
  pointer-events: none;
  cursor: not-allowed;
}

.s-tabs__button:hover {
  border-bottom: 0.25rem solid gray;

  /*  color: black; */
}

.s-tabs__button:focus {
  outline: none;
  border-bottom: 0.25rem solid black;
}
</style>