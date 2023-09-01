<template>
  <el-container>
    <el-tabs type="card" v-model="activeTab" @tab-click="handleClick">
      <el-tab-pane label="skiresortInformation" name="skiresortInformation">
        <el-table
        :data="skiresorts"
        stripe
        style="width: 100%"
        @row-click="selectRow"
        >
          <el-table-column
            prop="skiresortNo"
            label="スキーリゾート番号"
            width="180">
          </el-table-column>
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
      <el-tab-pane label="inputForm" name="inputForm">
        <el-form :label-position="labelPosition" label-width="100px" :model="formLabelAlign">
          <el-form-item label="SkiresortNo">
            {{ formLabelAlign.skiresortNo }}
          </el-form-item>
          <el-form-item label="SkiresortName">
            <el-input v-model="formLabelAlign.skiresortName"></el-input>
          </el-form-item>
          <el-form-item label="Area">
            <el-input v-model="formLabelAlign.area"></el-input>
          </el-form-item>
          <el-form-item label="Access">
            <el-input v-model="formLabelAlign.access"></el-input>
          </el-form-item>
          <el-form-item label="numberOfStars">
            <el-rate v-model="formLabelAlign.numberOfStars"></el-rate>
          </el-form-item>
          <el-form-item label="RecommendedPoint">
            <el-input v-model="formLabelAlign.recommendedPoint"></el-input>
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
      activeTab: 'skiresortInformation', // どのタブを選択しているかを保持
      currentComponentName: 'SkiresortInformation',
      formLabelAlign: {
        skiresortNo: '',
        skiresortName: '',
        area: '',
        access: '',
        numberOfStars: 0,
        recommendedPoint: ''
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
      const skiresort = { skiresortNo: 1, skiresortName: 'わん', area: 'わんわん', access: 'にゃん', numberOfStars: 3, recommendedPoint: 'ぴー' }
      this.skiresorts.push(skiresort)
    },
    handleClick (tab) {
      if (tab.label === 'skiresortInformation') {
        this.currentComponentName = 'SkiresortInformation'
      } else if (tab.label === 'inputForm') {
        this.currentComponentName = 'InputForm'
      }
    },
    onSubmit () {
      const existingIndex = this.skiresorts.findIndex(
        skiresort => skiresort.skiresortNo === this.formLabelAlign.skiresortNo
      )

      const newSkiresort = {
        skiresortNo: existingIndex === -1 ? this.skiresorts.length + 1 : this.formLabelAlign.skiresortNo,
        skiresortName: this.formLabelAlign.skiresortName,
        area: this.formLabelAlign.area,
        access: this.formLabelAlign.access,
        numberOfStars: this.formLabelAlign.numberOfStars,
        recommendedPoint: this.formLabelAlign.recommendedPoint
      }

      if (existingIndex !== -1) {
        // 該当の skiresortNo のデータが存在する場合は上書き
        this.$set(this.skiresorts, existingIndex, newSkiresort)
      } else {
        // 存在しない場合は配列に追加
        this.skiresorts.push(newSkiresort)
      }

      this.formLabelAlign = {
        skiresortNo: '',
        skiresortName: '',
        area: '',
        access: '',
        numberOfStars: 0,
        recommendedPoint: ''
      } // 入力欄をクリア

      this.activeTab = 'skiresortInformation'
      console.log('submit!')
    },
    selectRow (row) {
      this.formLabelAlign.skiresortNo = row.skiresortNo
      this.formLabelAlign.skiresortName = row.skiresortName
      this.formLabelAlign.area = row.area
      this.formLabelAlign.access = row.access
      this.formLabelAlign.numberOfStars = row.numberOfStars
      this.formLabelAlign.recommendedPoint = row.recommendedPoint

      this.activeTab = 'inputForm'
      console.log('test')
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
