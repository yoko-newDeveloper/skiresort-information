<template>
  <el-table
    :data="skiresorts"
    stripe
    style="width: 100%">
    <el-table-column
      prop="skiresortName"
      label="SkiresortName"
      width="180">
    </el-table-column>
    <el-table-column
      prop="area"
      label="Area"
      width="180">
    </el-table-column>
    <el-table-column
      prop="access"
      label="Access"
      width="180">
    </el-table-column>
    <el-table-column
      prop="numberOfStars"
      label="NumberOfStars"
      width="180">
    </el-table-column>
    <el-table-column
      prop="recommendedPoint"
      label="RecommendedPoint"
      width="180">
    </el-table-column>
  </el-table>
</template>

<script>
export default {
  data () {
    return {
      skiresorts: []
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
        const skiresort = { skiresortName: 'わん', area: 'わんわん', access: 'にゃん', numberOfStars: 'にゃんにゃん', recommendedPoint: 'ぴー' }
        this.skiresorts.push(skiresort)
      }
    }
  }
}
</script>
