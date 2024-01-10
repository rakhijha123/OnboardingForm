<template>
    <div>
      
      <div class="container">
        <div>
        <h1>Employee Orboarding Form </h1>
      </div>
    <el-form
      ref="ruleFormRef"
      :model="ruleForm"
      :rules="rules"
      label-width="120px"
      class="demo-ruleForm"
      :size="formSize"
      status-icon
    >
      <el-form-item label="Name" prop="name">
        <el-input  v-model="ruleForm.name"/>
      </el-form-item>
      <el-form-item label="Date of Birth" prop="name">
        <el-input v-model="ruleForm.dateOfBirth" />
      </el-form-item>
      <el-form-item label="Gender" prop="name">
        <el-input v-model="ruleForm.gender" />
      </el-form-item>
      <el-form-item label="Blood Group" prop="name">
        <el-input v-model="ruleForm.blood_Group" />
      </el-form-item>
      <el-form-item label="Marital Status" prop="name">
        <el-input v-model="ruleForm.marital_status" />
      </el-form-item>
      <el-form-item label="Personal Email " prop="name">
        <el-input v-model="ruleForm.personal_email_id" />
      </el-form-item>
      <el-form-item label="Phone Number" prop="name">
        <el-input v-model="ruleForm.alternate_phone_number" />
      </el-form-item>
      <el-form-item label="Alternate Phone Number" prop="name">
        <el-input v-model="ruleForm. alternate_phone_number" />
      </el-form-item>
      <el-form-item label="Current Address" prop="name">
        <el-input v-model="ruleForm.Current_address" />
      </el-form-item>
      <el-form-item label="Permanent Address" prop="name">
        <el-input v-model="ruleForm.Permanent_address" />
      </el-form-item>
      <el-form-item label="SOCIAL-PROFILE" prop="name">
        <el-input v-model="ruleForm.social_profile" />
      </el-form-item>
      <el-form-item>
        <!-- <el-button type="primary" @click="submitForm"
          >Submit</el-button> -->
          <el-button type="primary" @click="submitForm">Submit</el-button>
      </el-form-item>
    </el-form>
</div>
  </div>
  </template>
  
  <script lang="ts" setup>
  import { reactive, ref } from 'vue'
  import type { FormInstance, FormRules } from 'element-plus'
  
  interface OrboardingForm {
    name: string
    dateOfBirth: string
    gender: string
    blood_Group: string
    marital_status: string
    personal_email_id: string
    phone_number: string
    alternate_phone_number: string
    Current_address: string
    Permanent_address: string
    social_profile: string
  }
  
  const formSize = ref('default')
  const ruleFormRef = ref<FormInstance>()
  const ruleForm = reactive<OrboardingForm>({
    name: '',
    dateOfBirth: '',
    gender: '',
    blood_Group: '',
    marital_status: '',
    personal_email_id: '',
    phone_number: '',
    alternate_phone_number: '',
    Current_address: '',
    Permanent_address: '',
    social_profile: '',
  })
  
  const rules = reactive<FormRules<OrboardingForm>>({
    name: [
      { required: true, message: 'Please input Activity name', trigger: 'blur' },
      { min: 3, max: 5, message: 'Length should be 3 to 5', trigger: 'blur' },
    ],
    dateOfBirth: [
      {
        required: true,
        message: 'Please select Activity zone',
        trigger: 'change',
      },
    ],
    gender: [
      {
        required: true,
        message: 'Please select Activity count',
        trigger: 'change',
      },
    ],
    blood_Group: [
      {
        type: 'date',
        required: true,
        message: 'Please pick a date',
        trigger: 'change',
      },
    ],
    marital_status: [
      {
        type: 'date',
        required: true,
        message: 'Please pick a time',
        trigger: 'change',
      },
    ],
    personal_email_id: [
      {
        type: 'array',
        required: true,
        message: 'Please select at least one activity type',
        trigger: 'change',
      },
    ],
    phone_number: [
      {
        type: 'array',
        required: true,
        message: 'Please select at least one activity type',
        trigger: 'change',
      },
    ],
    alternate_phone_number: [
      {
        required: true,
        message: 'Please select activity resource',
        trigger: 'change',
      },
    ],
    Current_address: [
      { required: true, message: 'Please input activity form', trigger: 'blur' },
    ],
    Permanent_address: [
      { required: true, message: 'Please input activity form', trigger: 'blur' },
    ],
    social_profile: [
      { required: true, message: 'Please input activity form', trigger: 'blur' },
    ],
  })
  
//   const submitForm = async (formEl: FormInstance | undefined) => {
//     if (!formEl) return
//     await formEl.validate((valid, fields) => {
//       if (valid) {
//         console.log('submit!')
//       } else {
//         console.log('error submit!', fields)
//       }
//     })
//   }
const submitForm = async() => {
  if (!ruleFormRef.value) return;
  await ruleFormRef.value.validate((valid, fields) => {
    if (valid) {
      console.log('submit!');
    } else {
      console.log('error submit!', fields);
    }
  });
};
  
  const resetForm = (formEl: FormInstance | undefined) => {
    if (!formEl) return
    formEl.resetFields()
  }
  
  const options = Array.from({ length: 10000 }).map((_, idx) => ({
    value: `${idx + 1}`,
    label: `${idx + 1}`,
  }))
  </script>