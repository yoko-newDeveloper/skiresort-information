<template>
  <el-table
    :data="tableData"
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
    // イベントが発火するたびに
    // window.addEventListener("イベント名", 関数名)
  // DOMが呼び込まれたときに一回だけ
  // this.関数名()
  },
  methods: {
    reverseMessage: function () {
      console.log(this.skiresorts)
    }
  }
}
</script>
