<template>
  <div class="sdf">
    {{ params }}
  </div>
</template>

<script>
export default {
  name: "HomeView",
  props: {},
  data() {
    return {
      params: this.$route.params,
    };
  },
};
</script>
