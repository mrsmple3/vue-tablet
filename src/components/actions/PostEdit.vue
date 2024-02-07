<template>
  <div
    v-if="edit"
    class="flex justify-between w-full transition ease-in-out delay-75"
  >
    <div class="flex flex-col gap-2">
      <div class="flex w-96">
        <input
          v-model="post.title"
          class="border-solid border-blue-900 outline-blue-900 w-full border rounded p-2"
          type="text"
          placeholder="Edit Name"
        />
        <button
          @click="editName"
          class="border rounded border-blue-900 px-3 transition ease-in-out delay-75 hover:bg-blue-900 hover:text-white"
        >
          ✓
        </button>
      </div>

      <div class="flex">
        <input
          v-model="post.body"
          class="border-solid border-blue-900 outline-blue-900 w-full border rounded p-2"
          type="text"
          placeholder="Edit Desc..."
        />
        <button
          @click="editDescription"
          class="border rounded border-blue-900 px-3 transition ease-in-out hover:bg-blue-900 hover:text-white"
        >
          ✓
        </button>
      </div>
    </div>
    <my-button
      @click="deletePost"
      class="h-16 px-3 py-1 rounded self-center border border-solid border-blue-900 transition ease-in-out hover:bg-blue-900 hover:text-white"
    >
      🗑
    </my-button>
  </div>
  <button
    @click="toggleEdit"
    class="ml-6 animate-pulse h-16 px-3 py-1 rounded self-center border border-solid border-blue-900 transition ease-in-out hover:bg-blue-900 hover:text-white"
  >
    Edit
  </button>
</template>

<script>
import { ref } from "vue";
export default {
  props: {
    index: Number,
  },

  setup() {
    const edit = ref(false);

    function toggleEdit() {
      edit.value = !edit.value;
    }

    return {
      edit,
      toggleEdit,
    };
  },
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    deletePost() {
      this.$emit("deletePost", this.index);
    },

    editName() {
      this.$emit("editName", this.post, this.index);
    },
    editDescription() {
      this.$emit("editDescription", this.post, this.index);
    },
  },
};
</script>
