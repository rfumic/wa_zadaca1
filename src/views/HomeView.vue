<template>
  <h1 class="text-4xl m-2">Vue.js Commits</h1>
  <div class="flex flex-col items-center m-5 p-5">
    <div
      class="w-1/3 text-gray-900 bg-white rounded-lg border border-gray-200"
      v-for="commit in dataArray"
      :key="commit.sha"
      @click="goToDetails(commit)"
    >
      <button
        type="button"
        class="inline-flex relative items-center py-2 px-4 w-full text-xl font-medium rounded-t-lg border-b border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-2 focus:ring-blue-700 focus:text-blue-700"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="mr-2 w-4 h-4"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
          />
        </svg>
        {{ commit.sha }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  props: {},
  data() {
    return {
      dataArray: [],
    };
  },
  mounted() {
    this.getData();
  },
  methods: {
    async getData() {
      try {
        const response = await fetch(
          "https://api.github.com/repos/vuejs/vue/commits"
        );

        const result = await response.json();
        this.dataArray = result;
      } catch (err) {
        console.error(err);
      }
    },
    goToDetails(params) {
      this.$router.push({
        name: "DetailsView",
        params: {
          name: params.commit.author.name,
          email: params.commit.author.email,
          date: params.commit.author.date,
          sha: params.sha,
          message: params.commit.message,
        },
      });
    },
  },
};
</script>
