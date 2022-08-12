<template>
  <div>
    <span
      class="bi bi-trash-fill ms-3"
      role="button"
      @click="deleteTask"
    ></span>
    <span v-if="loading" class="spinner-border spinner-border-sm"></span>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
import { useStore } from "vuex";
export default {
  props: ["id"],
  setup(props) {
    const store = useStore();
    const loading = ref(false);
    async function deleteTask() {
      loading.value = true;
      await store.dispatch("task/deleteTask", props.id);
      loading.value = false;
    }
    return { loading, deleteTask };
  },
};
</script>

<style>
</style>