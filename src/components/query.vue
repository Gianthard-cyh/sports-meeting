<template>
  <v-container
    ><v-card class="ma-2">
      <v-card-title primary-title> 成绩查询 </v-card-title>
      <v-card-text>
        <v-btn-toggle v-model="toggle_exclusive" dense mandatory>
          <v-btn>
            <div>按班级</div>
          </v-btn>

          <v-btn>
            <div>按姓名</div>
          </v-btn>

          <v-btn>
            <div>按项目</div>
          </v-btn>
        </v-btn-toggle>
      </v-card-text>
    </v-card>
    <v-card class="ma-2">
      <v-card-text>
        <querybyclass v-show="toggle_exclusive == 0"></querybyclass>
        <querybyname v-show="toggle_exclusive == 1"></querybyname>
        <querybyproject v-show="toggle_exclusive == 2"> </querybyproject>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
import querybyclass from "./query_compoments/querybyclass";
import querybyname from "./query_compoments/querybyname.vue";
import Querybyproject from './query_compoments/querybyproject.vue';

export default {
  components: { querybyclass, querybyname, Querybyproject },
  data: () => ({
    toggle_exclusive: 0,
    grade_items: ["高一", "高二", "高三"],
  }),
};
</script>

<style>
</style>