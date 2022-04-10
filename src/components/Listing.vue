<script>
export default {
  props: {
    company: String,
    logo: String,
    isNew: Boolean,
    featured: Boolean,
    position: String,
    role: String,
    level: String,
    postedAt: String,
    contract: String,
    location: String,
    languages: Array,
    tools: Array,
    filter: Function,
  },
};
</script>
<template>
  <div
    :class="[
      isNew ? 'border-l-4' : '',
      'cursor-pointer md:flex-row md:justify-between hover:shadow-slate-300 transition duration-300 shadow-lg p-4 m-3 flex flex-col w-80 md:w-3/4 mx-auto rounded-md h-max-92 border-l-teal-600 relative space-y-6',
    ]"
  >
    <div class="flex flex-col gap-4 cursor-pointer">
      <img :src="logo" :alt="company" class="absolute md:static w-14 -top-8" />
      <div class="flex items-center gap-3 w-60 font-medium mt-4 md:mt-0">
        <h2 class="text-xs text-cyan-600 font-medium">{{ company }}</h2>
        <p
          v-if="isNew"
          style="font-size: x-small"
          class="bg-cyan-400 py-1 px-2 align-middle rounded-full text-white"
        >
          NEW!
        </p>
        <p
          v-if="featured"
          style="font-size: x-small"
          class="bg-gray-900 py-1 px-2 align-middle rounded-full text-white"
        >
          FEATURED
        </p>
      </div>
      <h2 class="text-md text-gray-900 font-semibold">{{ position }}</h2>
      <div class="w-2/3 md:w-full flex items-center justify-between">
        <span class="text-gray-400 text-xs">{{ postedAt }}--</span>
        <span class="text-gray-400 text-xs">{{ contract }}--</span>
        <span class="text-gray-400 text-xs">{{ location }}</span>
      </div>
      <hr class="border-gray-400 md:invisible" />
    </div>
    <div class="flex items-center gap-3 flex-wrap">
      <button
        @click="filter($event.target.value)"
        :value="role"
        class="cursor-pointer text-xs text-cyan-400 bg-cyan-100 hover:bg-cyan-500 hover:text-gray-100 p-2 transition duration-300 px-2 rounded-sm"
      >
        {{ role }}
      </button>
      <button
        @click="filter($event.target.value)"
        :value="level"
        class="cursor-pointer text-xs text-cyan-400 bg-cyan-100 hover:bg-cyan-500 hover:text-gray-100 p-2 transition duration-300 px-2 rounded-sm"
      >
        {{ level }}
      </button>
      <button
        @click="filter($event.target.value)"
        :value="lang"
        class="cursor-pointer text-xs text-cyan-400 bg-cyan-100 hover:bg-cyan-500 hover:text-gray-100 p-2 transition duration-300 px-2 rounded-sm"
        v-for="lang in languages"
        :key="lang"
      >
        {{ lang }}
      </button>
      <button
        @click="filter($event.target.value)"
        :value="tool"
        class="cursor-pointer text-xs text-cyan-400 bg-cyan-100 hover:bg-cyan-500 hover:text-gray-100 p-2 transition duration-300 px-2 rounded-sm"
        v-for="tool in tools"
        :key="tool"
      >
        {{ tool }}
      </button>
    </div>
  </div>
</template>
