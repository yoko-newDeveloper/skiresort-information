<template>
  <el-container>
    <el-tabs type="card" @tab-click="handleClick">
      <el-tab-pane label="skiresortInformation">
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

      </el-tab-pane>
      <el-tab-pane label="inputForm">
        <el-form :label-position="labelPosition" label-width="100px" :model="formLabelAlign">
          <el-form-item label="SkiresortName">
            <el-input v-model="formLabelAlign.name"></el-input>
          </el-form-item>
          <el-form-item label="Area">
            <el-input v-model="formLabelAlign.region"></el-input>
          </el-form-item>
          <el-form-item label="Access">
            <el-input v-model="formLabelAlign.type"></el-input>
          </el-form-item>
          <el-form-item label="numberOfStars">
            <el-input v-model="formLabelAlign.type"></el-input>
          </el-form-item>
          <el-form-item label="RecommendedPoint">
            <el-input v-model="formLabelAlign.type"></el-input>
          </el-form-item>
        </el-form>
        <el-button type="primary" @click="onSubmit">Submit</el-button>
        <el-button type="default" @click="onSubmit">Cancel</el-button>

      </el-tab-pane>
    </el-tabs>
</el-container>
</template>

<script>
// それぞれのコンポーネントをインポートする
// import SkiresortInformation from './SkiresortInformation.vue'
// import InputForm from './InputForm.vue'
export default {
  // components: { SkiresortInformation, InputForm },
  // selectedComponent: {
  //   SkiresortInformation,
  //   InputForm
  // },
  data () {
    return {
      skiresorts: [],
      activeTab: 'first',
      currentComponentName: 'SkiresortInformation',
      formLabelAlign: {
        name: '',
        region: '',
        type: ''
      },
      // postで送信するためのリクエストデータ初期化
      request: {
        name: ''
      }

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
    handleClick (tab) {
      if (tab.label === 'skiresortInformation') {
        this.currentComponentName = 'SkiresortInformation'
      } else if (tab.label === 'inputForm') {
        this.currentComponentName = 'InputForm'
      }
    },
    onSubmit () {
      console.log('submit!')
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
