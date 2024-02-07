<template>
  <div
    class="flex flex-row border rounded border-gray-900 p-5 items-center bg-gray-100"
    v-for="(post, index) in posts"
    :key="post.id"
  >
    <div class="flex flex-col gap-1 w-96">
      <h3>
        <strong>{{ post.id }}.Title:</strong> {{ post.title }}
      </h3>
      <p><strong>Description:</strong> {{ post.body }}</p>
    </div>
    <post-edit
      :index="index"
      @deletePost="deletePost(index)"
      @editName="editName"
      @editDescription="editDescription"
    />
  </div>
</template>

<script>
import PostEdit from "./actions/PostEdit.vue";
export default {
  components: {
    PostEdit,
  },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
  methods: {
    deletePost(index) {
      this.$emit("deletePost", index);
    },
    editName(post, index) {
      post.id = index;
      this.$emit("editName", post);
    },
    editDescription(post, index) {
      post.id = index;
      this.$emit("editDescription", post);
    },
  },
};
</script>

<style></style>
