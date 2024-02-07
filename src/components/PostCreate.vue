<template>
  <form @submit.prevent class="flex flex-col gap-3 items-start">
    <div class="flex flex-col gap-2 w-full">
      <my-input v-model="newPost.title" placeholder="Name" />
      <my-input v-model="newPost.body" type="text" placeholder="Description" />
    </div>
    <my-button @click="createPost">OK</my-button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newPost: {
        id: 0,
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      if (this.newPost.title === "") {
        return;
      }
      this.$emit("createPost", this.newPost);
      this.newPost = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style></style>
