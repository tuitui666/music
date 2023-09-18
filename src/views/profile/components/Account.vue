<template>
  <el-form>
    <el-form-item label="来取一个好听的昵称叭">
      <el-input v-model.trim="user.name" />
    </el-form-item>
    <el-form-item label="性别">
      <select v-model.trim="user.sex">
        <option disabled value="">--请选择--</option>
        <option>男♂</option>
        <option>女♀</option>
        <option>保密</option>
      </select>
    </el-form-item>
    <el-form-item label="留下你的邮箱">
      <el-input v-model.trim="user.email" />
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="submit">更新</el-button>
    </el-form-item>
  </el-form>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
      default: () => {
        return {
          name: '',
          email: '',
          sex: ''
        }
      }
    }
  },
  methods: {
    submit() {
      this.$message({
        message: 'User information has been updated successfully',
        type: 'success',
        duration: 5 * 1000
      })
    }
  }
}
</script>
