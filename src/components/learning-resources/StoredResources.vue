<template>
  <ul>
    <learning-resource
      v-for="res in resources"
      :key="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
    >
    </learning-resource>
  </ul>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import LearningResource from './LearningResource.vue';
export default defineComponent({
  props: ['resources'],
  components: { LearningResource },
});
</script>

<style scoped lang="scss">
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
