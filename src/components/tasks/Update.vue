<template>
  <div>
    <span
      v-if="task.completed"
      class="bi bi-check-all "
      role="button"
      style="font-size: 22px"
      @click="updateTask(task)"
    ></span>
    <span
      v-else
      class="bi bi-check"
      role="button"
      style="font-size: 22px"
      @click="updateTask(task)"
    ></span>
    <span v-if="loading" class="spinner-border spinner-border-sm"></span>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
import { useStore } from "vuex";
export default {
  props: ["task"],
  setup() {
    const store = useStore();
    const loading = ref(false);
    async function updateTask(task) {
      loading.value = true;
      await store.dispatch("task/updateTask", task);
      loading.value = false;
    }

    return { loading, updateTask };
  },
};
</script>

<style>
</style>