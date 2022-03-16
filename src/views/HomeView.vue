<template>
  <h1 class="text-4xl">Vue.js Commits</h1>
  <div class="bg-blue-200 flex flex-col items-center m-5 p-5">
    <div
      class="border border-black w-1/2 m-1 bg-white text-xl hover:cursor-pointer hover:text-blue-500"
      v-for="commit in dataArray"
      :key="commit.sha"
      @click="goToDetails(commit)"
    >
      {{ commit.sha }}
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
        console.log(result);
        this.dataArray = result;
      } catch (err) {
        console.error(err);
      }
    },
    goToDetails(params) {
      console.log(params);
      this.$router.push({
        name: "DetailsView",
        params: params,
      });
    },
  },
};
</script>
