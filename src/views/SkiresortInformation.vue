<template>
  <el-container>
  <el-header>skiresortInformation</el-header>
  <el-tabs type="card" @tab-click="handleClick">
    <el-tab-pane label="skiresortInformation"></el-tab-pane>
    <el-tab-pane label="inputForm"></el-tab-pane>

    <component :is="currentComponentName"></component>
  </el-tabs>
  <el-main>
    <el-table
      :data="skiresorts"
      stripe
      style="width: 100%">
      <el-table-column
        prop="skiresortName"
        label="スキーリゾート名"
        width="180">
      </el-table-column>
      <el-table-column
        label="エリア"
        width="180">
        <template slot-scope="scope">
          {{ scope.row.area }} ken
        </template>
      </el-table-column>
      <el-table-column
        prop="access"
        label="行き方"
        width="180">
      </el-table-column>
      <el-table-column
          label="星の数"
          width="180">
          <template slot-scope="scope">
            <el-rate v-model="scope.row.numberOfStars"></el-rate>
          </template>
        </el-table-column>
      <el-table-column
        label="おすすめポイント"
        width="180">
        <template slot-scope="scope">
          ❤️ {{ scope.row.recommendedPoint }}
        </template>
      </el-table-column>
    </el-table>
  </el-main>
</el-container>
</template>

<script>
// それぞれのコンポーネントをインポートする
import SkiresortInformation from './SkiresortInformation.vue'
import InputForm from './InputForm.vue'
export default {
  components: { SkiresortInformation, InputForm },
  data () {
    return {
      skiresorts: [],
      activeName: 'first',
      selectedComponent: 'default'
    }
  },
  mounted () {
    console.log('画面開いたよ')
    this.showSkiresorts()
    // イベントが発火するたびに
    // window.addEventListener("イベント名", 関数名)
  // DOMが呼び込まれたときに一回だけ
  // this.関数名()
  },
  methods: {
    showSkiresorts: function () {
      for (let i = 0; i < 3; i++) {
        const skiresort = { skiresortName: 'わん', area: 'わんわん', access: 'にゃん', numberOfStars: 3, recommendedPoint: 'ぴー' }
        this.skiresorts.push(skiresort)
      }
    },
    handleClick (tab, event) {
      console.log(tab, event)
    }
  }
}
</script>
<style>
  .el-header  {
    background-color: #e27dd8;
    color: white;
    text-align: center;
    line-height: 60px;
    width: auto;
    font-weight: bold;
    font-size: 25px;
  }
</style>
