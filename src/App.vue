<template>
  <h1>Früchte Zähler</h1>
  <p>Gesamtanzahl an Früchten: {{ totalFruitCount }}</p>
  <div>
    <Counter
      v-for="fruitCounter in fruitCounters"
      :key="fruitCounter.id"
      :title="fruitCounter.title"
      :emoji="fruitCounter.emoji"
      @count-up="handleCount"
    />
  </div>
</template>

<script>
import Counter from "./components/Counter.vue";

export default {
  name: "App",
  components: {
    Counter,
  },
  data() {
    return {
      fruitCounters: [
        {
          id: 1,
          title: "Mango",
          emoji: "🥭",
          count: 0,
        },
        {
          id: 2,
          title: "Apfel",
          emoji: "🍎",
          count: 0,
        },
        {
          id: 3,
          title: "Banane",
          emoji: "🍌",
          count: 0,
        },
      ],
    };
  },
  computed: {
    totalFruitCount() {
      let totalCount = 0;

      this.fruitCounters.forEach((counter) => {
        totalCount += counter.count;
      });

      return totalCount;
    },
  },
  methods: {
    handleCount(title) {
      const index = this.fruitCounters.findIndex(
        (counter) => counter.title === title
      );
      console.log(index);
      this.fruitCounters[index].count++;
    },
  },
};
</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
}
</style>
