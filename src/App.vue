<template>
  <s-tabs>
    <s-tab title="Tab 1">Content Tab 1</s-tab>
    <s-tab title="Tab 2">Content Tab 2</s-tab>
    <s-tab title="Tab 3">Content Tab 3</s-tab>
    <s-tab title="Tab 4" disabled>Content Tab 4</s-tab>
  </s-tabs>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { STabs, STab } from './components/STabs'

export default defineComponent({
  name: 'App',
  components: {
    STabs,
    STab
  }
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
