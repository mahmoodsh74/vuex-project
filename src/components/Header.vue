<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light shadow-sm">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Parvazco.com</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <router-link class="nav-link" to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/tasks">Tasks</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/products">Products</router-link>
          </li>
        </ul>
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <router-link class="nav-link" to="/cart">
              <span class="badge rounded-pill bg-primary me-1">{{
                countCartItem
              }}</span>
              <i class="bi bi-basket-fill" style="font-size: 23px"></i>
            </router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
import { computed } from "@vue/runtime-core";
import { useStore } from "vuex";
export default {
  name: "Header",
  setup() {
    const store = useStore();
    const countCartItem = computed(() => store.getters["cart/count"]);
    return { countCartItem };
  },
};
</script>

<style scoped>
.router-link-active {
  color: rgba(0, 0, 0, 0.9) !important;
  border-bottom: 2px solid rgba(0, 0, 0, 0.9) !important;
}
</style>