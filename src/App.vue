<template>
  <div class="content">
    <a-card style="width: 300px" title="左侧">
      <ul>
        <li v-for="item in leftData" :key="item.title">
          <input type="checkbox" v-model="item.isCheck" />
          <label>{{ item.title }}</label>
        </li>
      </ul>
    </a-card>

    <div class="btn-group">
      <button @click="shuttle(0)">→</button>
      <button @click="shuttle(1)">←</button>
    </div>

    <a-card style="width: 300px" title="右侧">
      <ul>
        <li v-for="item in rightData" :key="item.title">
          <input type="checkbox" v-model="item.isCheck" />
          <label>{{ item.title }}</label>
        </li>
      </ul>
    </a-card>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from "vue";
export default defineComponent({
  name: "App",
  components: {},
  setup() {
    const state = reactive({
      leftData: [
        {
          title: "furfur-jiang-left",
          isCheck: true,
        },
        {
          title: "fur-left",
          isCheck: true,
        },
        {
          title: "furfur-left",
          isCheck: false,
        },
        {
          title: "furfurJiang-left",
          isCheck: false,
        },
      ],
      rightData: [
        {
          title: "furfur-jiang-right",
          isCheck: true,
        },
      ],
    });

    const shuttle = (flag: number) => {
      if (flag === 0) {
        state.rightData = [
          ...state.rightData,
          ...state.leftData.filter((item) => item.isCheck),
        ];
        state.leftData = state.leftData.filter((item) => !item.isCheck);
      }else{
        state.leftData = [
          ...state.leftData,
          ...state.rightData.filter((item) => item.isCheck),
        ];
        state.rightData = state.rightData.filter((item) => !item.isCheck);
      }
    };
    return {
      ...toRefs(state),
      shuttle,
    };
  },
});
</script>

<style scoped>
.content {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 15px;
}
.btn-group {
  display: flex;
  flex-direction: column;
  margin: 15px;
}
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>
