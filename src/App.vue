<script>
import Listing from "./components/Listing.vue";
import Filter from "./components/Filter.vue";
import Data from "./data.json";
export default {
  data() {
    return {
      jobs: [],
      revert: this.revert,
      currFilter: "",
      message: "Result Not Found",
      filter: (filterValue) => {
        if (filterValue === "all") {
          this.currFilter = "";
          return this.jobs;
        } else {
          this.jobs = Data.filter(
            (job) =>
              job.role === filterValue ||
              job.level === filterValue ||
              job.languages.includes(filterValue) ||
              job.tools.includes(filterValue)
          );
          this.currFilter = filterValue;
        }
      },
    };
  },
  methods: {
    revert() {
      this.jobs = Data;
    },
  },

  mounted() {
    this.jobs = Data;
  },
  components: { Listing, Filter },
};
</script>

<template>
  <header class="w-full h-36"></header>
  <main class="space-y-20 py-12">
    <Filter
      :filter="filter"
      :revert="revert"
      :jobs="jobs"
      :currFilter="currFilter"
    />
    <h2
      v-if="jobs.length === 0"
      class="text-center text-cyan-700 font-bold text-lg"
    >
      {{ message }}
    </h2>
    <p
      v-if="jobs.length === 0"
      @click="revert"
      class="underline text-center cursor-pointer text-cyan-400"
    >
      Remove Filter
    </p>
    <div v-for="job in this.jobs" :key="job">
      <Listing v-bind="job" :filter="filter" />
    </div>
  </main>
</template>

<style>
header {
  background-image: url("./components/icons/bg-header-mobile.svg");
  background-repeat: no-repeat;
  background-color: hsl(180, 29%, 50%);
}
@media screen and (min-width: 376px) {
  header {
    background-image: url("./components/icons/bg-header-desktop.svg");
  }
}
</style>
