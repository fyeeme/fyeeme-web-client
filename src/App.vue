<script setup lang="ts">
import { findIndex } from "@fyeeme/util";
import { userApi, productApi, commentApi, categoryApi } from "@fyeeme/api";
import { onMounted, ref } from "vue";
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from "./components/HelloWorld.vue";

const arr: string[] = ["a", "2", "b"];

const index = ref<number>(0);

const getUser = (id: number) => {
  userApi
    .get(id)
    .then((res) => {
      console.log(res.data);
    })
    .catch((err) => {
      console.log("error:", err);
    });
};

const getProduct = (id: number) => {
  productApi.get(id).then((res) => {
    console.log({ res });
  });
};
onMounted(() => {
  index.value = findIndex(arr, "b");
  getUser(5);
  getUser(10);
  getProduct(6);
});
</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
  index is {{ index }}
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
