<template>
  <div class="row">
    <div class="col-md-12 mb-4">
      <h4>Create Tasks :</h4>
      <form @submit.prevent="storeTask" class="row">
        <div class="col-md-6">
          <input v-model="title" class="form-control" type="text" />
          <div class="form-text text-danger">{{ titleErrorText }}</div>
        </div>
        <div class="col-auto">
          <button class="btn btn-dark">
            Create
            <span
              v-if="loading"
              class="spinner-border spinner-border-sm"
            ></span>
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
import { useStore } from "vuex";
export default {
  setup() {
    const store = useStore();
    const title = ref("");
    const titleErrorText = ref("");
    const loading = ref(false);

    async function storeTask() {
      if (title.value == "") {
        titleErrorText.value = "Title is required";
      } else {
        loading.value = true;
        titleErrorText.value = "";
        await store.dispatch("task/storeTask", title.value);
        loading.value = false;
        title.value = "";
      }
    }

    return { title, storeTask, titleErrorText, loading };
  },
};
</script>

<style>
</style>