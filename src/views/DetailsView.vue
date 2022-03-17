<template>
  <h1 class="text-4xl m-2">Vue.js Commit Details</h1>
  <div class="flex m-4">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      class="h-10 w-10 hover:cursor-pointer hover:text-blue-700"
      fill="none"
      viewBox="0 0 24 24"
      stroke="currentColor"
      stroke-width="2"
      @click="$router.go(-1)"
    >
      <path
        stroke-linecap="round"
        stroke-linejoin="round"
        d="M11 15l-3-3m0 0l3-3m-3 3h8M3 12a9 9 0 1118 0 9 9 0 01-18 0z"
      />
    </svg>
  </div>
  <div class="flex flex-col m-5 p-5 items-center">
    <div
      class="w-1/3 text-gray-900 bg-white rounded-lg border border-gray-200 p-3"
    >
      <div class="text-xl leading-none text-gray-900">
        {{ params.sha }}
      </div>
      <div class="flow-root">
        <ul role="list" class="divide-y divide-gray-200">
          <li class="py-3 sm:py-4">
            <div class="flex items-center space-x-4">
              <div class="flex-1 min-w-0">
                <p class="font-medium text-gray-900">Name</p>
                <p class="text-gray-500">{{ params.name }}</p>
              </div>
            </div>
          </li>
          <li class="py-3 sm:py-4">
            <div class="flex items-center space-x-4">
              <div class="flex-1 min-w-0">
                <p class="font-medium text-gray-900">Email</p>
                <p class="text-gray-500">{{ params.email }}</p>
              </div>
            </div>
          </li>
          <li class="py-3 sm:py-4">
            <div class="flex items-center space-x-4">
              <div class="flex-1 min-w-0">
                <p class="font-medium text-gray-900">Message</p>
                <p class="text-gray-500">{{ params.message }}</p>
              </div>
            </div>
          </li>
          <li class="py-3 sm:py-4">
            <div class="flex items-center space-x-4">
              <div class="flex-1 min-w-0">
                <p class="font-medium text-gray-900">Date</p>
                <p class="text-gray-500">{{ params.date }}</p>
              </div>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DetailsView",
  props: {},
  data() {
    return {
      params: this.$route.params,
    };
  },
};
</script>
