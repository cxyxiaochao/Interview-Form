<template>
  <div class="employee-search">
    <h2>查询员工应聘登记信息</h2>
    <form @submit.prevent="searchEmployees" class="form-container">
      <el-form-item label="身份证号:">
        <el-input v-model="searchCriteria.idCard" placeholder="身份证号" clearable />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" :plain="true" @click="searchEmployees">查询</el-button>
      </el-form-item>
    </form>
  </div>

  <el-table :data="employees" style="max-width: 100%;margin-top: 10px;text-align: center;" height="640" border>
    <el-table-column fixed prop="birthday" label="时间" width="150" />
    <el-table-column fixed prop='name' label="姓名" width="140" />
    <el-table-column prop="sex" label="性别" width="60" />
    <el-table-column prop="bloodType" label="血型" width="60" />
    <el-table-column prop="birthday" label="生日" width="120" />
    <el-table-column prop="nation" label="民族" width="60" />
    <el-table-column prop="height" label=" 身高(cm)" width="60" />
    <el-table-column prop="weight" label="体重(kg)" width="60" />
    <el-table-column prop="nativePlace" label="籍贯" width="60" />
    <el-table-column prop="maritalStatus" label="婚姻状态" width="60" />
    <el-table-column prop="politicsStatus" label="政治面貌" width="120" />
    <el-table-column prop="religion" label=" 宗教信仰" width="120" />
    <el-table-column prop="constellation" label="星座" width="120" />
    <el-table-column prop="school" label="毕业学校" width="120" />
    <el-table-column prop="degrees" label="学历" width="120" />
    <el-table-column prop="soecialty" label="专业" width="120" />
    <el-table-column prop="idCard" label="身份证号" width="400" />
    <el-table-column prop="tel" label="手机号" width="120" />
    <el-table-column prop="phone" label="家庭电话" width="120" />
    <el-table-column prop="idCardAddress" label="身份证地址" width="120" />
    <el-table-column prop="nowAddress" label="现居住地址" width="120" />
    <el-table-column prop="ifDispute" label="是否和前单位有纠纷" width="120" />
    <el-table-column prop="ifDisputeRemark" label="纠纷备注说明" width="450" />
    <el-table-column prop="ifFire" label="是否因工作或品行被解雇" width="450" />
    <el-table-column prop="ifFireRemark" label="解雇备注说明" width="450" />
    <el-table-column prop="ifCrime" label="是否有犯罪记录" width="450" />
    <el-table-column prop="ifCrimeRemark" label="犯罪备注说明" width="450" />
    <el-table-column prop="ifNoSalary" label="是否接受新人三天离职无薪" width="450" />
    <el-table-column prop="ifSingleDayWeekend" label="是否接受单休" width="450" />
    <el-table-column prop="ifWorkOvertime" label="是否接受加班" width="450" />
    <el-table-column prop="workStatus" label="目前工作状态" width="450" />
    <el-table-column prop="ifDrive" label="是否会驾驶" width="450" />
    <el-table-column prop="certificate" label="入职能提供的证明" width="450" />
    <el-table-column prop="salary" label="试用期薪资要求" width="450" />
    <el-table-column prop="workingHours" label="到岗时间" width="450" />

    <el-table-column prop="employeeFamilyInformationFormList" label="员工家庭信息集合" width="500">
      <el-table-column prop="staffId" label="员工id" width="150" />
      <el-table-column prop="staffName" label="员工姓名" width="150" />
      <el-table-column prop="familyRelationships" label="家庭关系" width="150" />
      <el-table-column prop="name" label="姓名" width="150" />
      <el-table-column prop="age" label="年龄" width="150" />
      <el-table-column prop="tel" label="电话" width="150" />
      <el-table-column prop="occupation" label="职业" width="150" />
      <el-table-column prop="address" label="详细地址" width="150" />
    </el-table-column>

    <el-table-column prop="employeeWorkExperienceFormList" label="员工工作信息集合" width="500">
      <el-table-column prop="staffId" label="员工id" width="150" />
      <el-table-column prop="staffName" label="员工姓名" width="150" />
      <el-table-column prop="workTime" label="工作时间" width="150" />
      <el-table-column prop="workUnitName" label="工作单位名称" width="150" />
      <el-table-column prop="salary" label="薪资" width="150" />
      <el-table-column prop="supervisorName" label="主管姓名" width="150" />
      <el-table-column prop="supervisorTel" label="主管手机号" width="150" />
      <el-table-column prop="resignationTimeAndReason" label="离职时间和原因" width="150" />
    </el-table-column>

    <el-table-column prop="employeeEducationAndTrainingSituationTables" label="员工教育培训情况集合" width="500">
      <el-table-column prop="staffId" label="员工id" width="150" />
      <el-table-column prop="staffName" label="员工姓名" width="150" />
      <el-table-column prop="shcool" label="学校、机构名称" width="150" />
      <el-table-column prop="degrees" label="学历" width="150" />
      <el-table-column prop="graduationDate" label="毕业日期" width="150" />
      <el-table-column prop="certName" label="证书名称" width="150" />
    </el-table-column>
  </el-table>
</template>

<script setup>
import { reactive, ref, onMounted } from 'vue';
import axios from 'axios';

const searchCriteria = reactive({
  idCard: ''
});

const employees = ref([]);

const searchEmployees = async () => {
  try {
    const response = await axios.post('/api/employeeRecruitmentRegistrationForm/getAllData', searchCriteria);
    employees.value = response.data;
  } catch (error) {
    console.error('Error:', error);
    employees.value = [];
  }
};

const fetchEmployees = async () => {
  try {
    const response = await axios.get('/api/employeeRecruitmentRegistrationForm/getAllDataTwo')
    employees.value = response.data;
  } catch (error) {
    console.error('Error fetching employees', error)
  }
}

onMounted(()=>{
  fetchEmployees();
});
</script>


<style scoped>
.employee-search {
  max-width: 100%;
  padding: 20px;
  margin-top: 26px;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  background-color: #fff;
}

h2 {
  text-align: center;
  color: #333;
}

.form-container {
  display: flex;
  flex-direction: column;
  gap: 15px;
  margin-bottom: 20px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.form-group label {
  font-weight: bold;
  color: #555;
}

.form-group input {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 14px;
  transition: border-color 0.3s;
}

.form-group input:focus {
  border-color: #4CAF50;
}

button{
  margin: auto;
}

.result-container {
  margin-top: 20px;
}

table {
  width: 100%;
  border-collapse: collapse;
}

thead th {
  background-color: #f2f2f2;
  padding: 10px;
  border-bottom: 1px solid #ddd;
}

tbody td {
  text-align: center;
  padding: 10px;
  border-bottom: 1px solid #ddd;
}

.no-result {
  text-align: center;
  color: #666;
  margin-top: 20px;
}
</style>