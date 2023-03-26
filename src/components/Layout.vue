<template>
  <el-container>
    <el-aside><my-header /></el-aside>
    <el-main><slot></slot></el-main>
  </el-container>
</template>

<script>
import { useRoute } from "vue-router";
import { onMounted, ref } from "vue";
import Header from "./Header";

export default {
  name: "App",
  components: { "my-header": Header,  },
  setup() {
    const route = useRoute();
    const footerShow = ref(true);
    onMounted(() => {
      switch (route.path) {
        case "/docs":
          footerShow.value = false;
          break;
        case "/utils":
          footerShow.value = false;
          break;
        default:
          footerShow.value = true;
          break;
      }
    });
    return { footerShow };
  },
};
</script>