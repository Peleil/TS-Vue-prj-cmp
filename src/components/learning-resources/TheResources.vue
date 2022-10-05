<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resources</base-button
    >
  </base-card>
  <component :is="selectedTab"></component>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default defineComponent({
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation.',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://google.org',
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
    };
  },
  methods: {
    setSelectedTab(tab: string): void {
      this.selectedTab = tab;
    },
  },
  computed: {
    storedResButtonMode(): null | string {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResButtonMode(): null | string {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },
});
</script>
