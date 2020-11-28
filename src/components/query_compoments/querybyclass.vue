<template>
  <div class="class">
    <v-row>
      <v-col>
        <v-select
          :items="grade_items"
          item-text="text"
          item-value="value"
          v-model="grade_selection"
          label="年级"
          flat
        ></v-select
      ></v-col>
      <v-col>
        <v-select
          :items="class_items"
          item-text="text"
          item-value="value"
          label="班级"
          flat
        ></v-select
      ></v-col>
      <v-col
        class="mt-3"
        width="10px"
        style="max-width: 170px"
        v-show="wl_show"
      >
        <v-btn-toggle v-model="toggle_wl" dense mandatory>
          <v-btn>
            <div>文</div>
          </v-btn>

          <v-btn>
            <div>理</div>
          </v-btn>
        </v-btn-toggle>
      </v-col>
    </v-row>
    <v-btn color="info" style="">查询</v-btn>
  </div>
</template>

<script>
export default {
  data: () => ({
    grade_selection: 1,
    grade_items: [
      { text: "高一", value: 1 },
      { text: "高二", value: 2 },
      { text: "高三", value: 3 },
    ],
    wl_show: false,
    toggle_wl: 0,
  }),

  watch: {
    grade_selection: function () {
      if (this.grade_selection >= 2) {
        this.wl_show = true;
      } else {
        this.wl_show = false;
      }
    },
  },

  computed: {
    class_items: function () {
      let res = [];
      switch (this.grade_selection) {
        case 1: {
          for (var i = 1; i <= 18; i++) {
            res.push({ text: i.toString() + "班", value: i });
          }
          break;
        }
        default: {
          for (var ii = 1; ii <= 18; ii++) {
            res.push({ text: ii.toString() + "班", value: ii });
          }
        }
      }
      return res;
    },
  },
};
</script>

<style>
</style>