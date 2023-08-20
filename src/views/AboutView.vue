<template>
  <div id="app">
    <input type="text"
      v-on:keydown.enter="onKeyDown" />
    <div>
      {{message}}
    </div>
    <el-radio-group v-model="labelPosition" size="small">
      <el-radio-button label="left">Left</el-radio-button>
      <el-radio-button label="right">Right</el-radio-button>
      <el-radio-button label="top">Top</el-radio-button>
    </el-radio-group>
    <div style="margin: 20px;"></div>
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
</div>
</template>
<script>
export default {
  data () {
    return {
      labelPosition: 'right',
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
  methods: {
    onSubmit () {
      console.log('submit!')
    },
    editName () {
      // リクエストデータに入力値を代入
      this.request.name = this.name
      // axiosでリクエストデータ送信
      // axios.post('/about', this.request).then(res => {
      //   console.log(res.data)
      // })
    }
  }
}
</script>
