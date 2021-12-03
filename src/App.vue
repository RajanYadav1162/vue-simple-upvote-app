<template>
  <div class="bg-gray-200">
    <h1 class="text-2xl font-bold text-center pt-10 italic text-red-500">
      UPVOTE VUE APP
    </h1>
    <hr class="mt-10 bg-green-500 w-full h-1" />
    <div class="flex flex-col justify-center items-center w-full py-10">
      <div
        v-for="item in sortedData"
        :key="item.id"
        class="
          main-container
          bg-gray-100
          flex
          my-8
          p-3
          items-center
          border border-red-300
          mx-4
          max-w-xl
          hover:shadow-xl hover:border-green-500
        "
      >
        <img :src="item.submissionImage" class="w-20 h-20" alt="" />
        <div class="content ml-4 flex flex-col">
          <h2 class="title text-lg font-semibold text-red-400 uppercase">
            {{ item.title }}
          </h2>
          <p class="text-gray-700 font-semibold text-medium tracking-wide my-2">
            {{ item.description }}
          </p>
          <div class="avatar flex items-center">
            <p class="text-gray-600 text-sm font-bold">Submitted By :</p>
            <img
              :src="item.avatar"
              class="w-10 h-10 rounded-full object-center object-cover"
              alt=""
            />
          </div>
        </div>

        <a
          href="#"
          class="flex hover:text-green-500 active:text-red-700"
          v-on:click="increase(item.id)"
        >
          <h3 class="vote text-xl tracking-widest font-bold">
            {{ item.votes }}
          </h3>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M5 10l7-7m0 0l7 7m-7-7v18"
            />
          </svg>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import data from './data/submissions';
export default {
  data() {
    return {
      data,
    };
  },

  computed: {
    sortedData: function () {
      return this.data.sort((a, b) => b.votes - a.votes);
    },
  },

  methods: {
    increase: function (id) {
      const item = this.data.find((target) => target.id === id);
      item.votes++;
    },
  },
};
</script>
