<template>
  <div
    class="flex md:gap-6 gap-3 flex-col md:flex-row items-center justify-end -mb-12"
  >
    <p class="text-red-400">
      {{ jobs.length }} {{ currFilter + (jobs.length > 1 ? " Jobs" : " Job") }}
    </p>
    <p @click="revert" class="underline cursor-pointer text-cyan-400">
      Remove Filter
    </p>
    <label for="select" class="float-right md:mr-12 p-3 border-none"
      >Filter:

      <select id="select" @change="filter($event.target.value)" class="md:ml-3">
        <option value="all">All</option>
        <option value="Frontend">Frontend</option>
        <option value="Backend">Backend</option>
        <option value="Fullstack">FullStack</option>
        <option value="Junior">Junior</option>
        <option value="Senior">Senior</option>
        <option value="Midweight">Midweight</option>
        <option value="HTML">HTML</option>
        <option value="CSS">CSS</option>
        <option value="Sass">Sass</option>
        <option value="JavaScript">JavaScript</option>
        <option value="React">React</option>
        <option value="Python">Python</option>
        <option value="Django">Django</option>
        <option value="Ruby">Ruby</option>
        <option value="RoR">RoR</option>
        <option value="Vue">Vue</option>
      </select>
    </label>
  </div>
</template>
<script>
export default {
  props: {
    filter: Function,
    revert: Function,
    jobs: Array,
    currFilter: String,
  },
};
</script>
