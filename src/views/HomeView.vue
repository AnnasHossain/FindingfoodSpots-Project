<template>
  <div class="home">
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
    return {
      items: []
    };
  },
  async mounted() {
    await this.loadData();
  },
  methods: {
    async loadData() {
      try {
        const response = await fetch('/api/items');
        if (response.ok) {
          this.items = await response.json();
        } else {
          console.error('Fehler beim Laden der Daten');
        }
      } catch (error) {
        console.error(error);
      }
    }
  }
};
</script>