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
import {
  defineComponent,
  reactive,
  toRefs,
  onRenderTracked,
  onRenderTriggered,
} from "vue";

export default defineComponent({
  name: "About",
  setup() {
    const data = reactive({
      books: ["星辰变", "盘龙", "斗破苍穹"],
      selectBook: "",
      selectBookFun: () => {
        let ranNum = Math.floor(Math.random() * 3);
        data.selectBook = data.books[ranNum];
      },
    });
    onRenderTracked((event) => {
      console.log(event);
    });
    onRenderTriggered((event) => {
      console.log("onRenderTriggered:");
      console.log(event);
    });
    const refData = toRefs(data);
    return {
      ...refData,
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
