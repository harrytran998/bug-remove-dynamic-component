<template>
  <el-row>
    <el-col :span="12">
      <el-form
        :model="tempAge"
        ref="forms"
        label-width="100px"
        class="demo-ruleForm"
      >
        <el-form-item
          label="age"
          prop="age"
          :rules="[
            { required: true, message: 'age is required' },
            { type: 'number', message: 'age must be a number' },
          ]"
        >
          <el-input
            type="age"
            v-model.number="tempAge.age"
            autocomplete="off"
          ></el-input>
        </el-form-item>
      </el-form>
    </el-col>
    <el-col :span="12">
      <i class="el-icon-delete" @click="deleteForm"></i>
    </el-col>
  </el-row>
</template>

<script>
export default {
  name: 'Form',
  created() {
    this.tempAge.age = this.age
  },
  data() {
    return {
      tempAge: {
        age: null,
      },
    }
  },
  methods: {
    deleteForm() {
      this.$emit('deleteForm', this.indexForm)
      console.log(this.indexForm)
    },
  },
  props: {
    age: {
      type: Number,
      required: true,
      default: 1,
    },
    indexForm: {
      type: Number,
      required: true,
    },
  },
}
</script>
