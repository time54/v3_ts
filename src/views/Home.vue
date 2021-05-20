<template>
  <div class="home">
    <div>
      我的书架:
      <div class="my-book" v-for="(item, idx) in books" :key="idx">
        {{ item }}
      </div>
    </div>
    <div>
      <button @click="selectBookFun">选择一本小说：</button>
      {{ selectBook }}
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "Home",
  setup() {
    const books = ref(["星辰变", "盘龙", "斗破苍穹"]);
    const selectBook = ref("");
    const selectBookFun = () => {
      let ranNum = Math.floor(Math.random() * 3);
      selectBook.value = books.value[ranNum];
    };
    return {
      books,
      selectBook,
      selectBookFun,
    };
  },
});
</script>
<style scoped>
.my-book {
  display: inline-block;
  margin-right: 20px;
}
</style>
