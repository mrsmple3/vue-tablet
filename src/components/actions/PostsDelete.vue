<template>
  <div>
    <my-button
      class="text-white bg-red-500 border rounded border-solid border-white transition ease-linear delay-75 hover:opacity-80"
      @click="deleteShiftPosts"
    >
      Delete
    </my-button>
  </div>
</template>

<script>
export default {
  methods: {
    deleteShiftPosts() {
      this.$emit("deletePosts");
    },
  },
};
</script>
