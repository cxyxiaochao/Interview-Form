<template>
  <el-form :inline="true" :model="form" class="demo-form-inline">
    <el-form-item label="姓名:">
      <el-input v-model="form.name" placeholder="姓名" clearable />
    </el-form-item>
    <el-form-item label="性别:">
      <el-select v-model="form.sex" placeholder="性别" clearable>
        <el-option label="男" value="0" />
        <el-option label="女" value="1" />
      </el-select>
    </el-form-item>
    <el-form-item label="血型:">
      <el-select v-model="form.bloodType" placeholder="血型" clearable>
        <el-option label="A" value="A" />
        <el-option label="B" value="B" />
        <el-option label="AB" value="AB" />
        <el-option label="O" value="O" />
      </el-select>
    </el-form-item>
    <el-form-item label="生日:">
      <div class="demo-date-picker">
        <el-date-picker v-model="form.birthday" type="date" placeholder="生日" format="YYYY/MM/DD"
          value-format="YYYY-MM-DD">
          <template #default="cell">
            <div class="cell" :class="{ current: cell.isCurrent }">
              <span class="text">{{ cell.text }}</span>
              <span v-if="isHoliday(cell)" class="holiday" />
            </div>
          </template>
        </el-date-picker>
      </div>
    </el-form-item>
    <el-form-item label="民族:">
      <el-input v-model="form.nation" placeholder="民族" clearable />
    </el-form-item>
    <el-form-item label="身高:">
      <el-input v-model="form.height" placeholder="身高" clearable />
    </el-form-item>
    <el-form-item label="体重:">
      <el-input v-model="form.weight" placeholder="体重" clearable />
    </el-form-item>
    <el-form-item label="籍贯:">
      <el-input v-model="form.nativePlace" placeholder="籍贯" clearable />
    </el-form-item>
    <el-form-item label="婚姻状态:">
      <el-select v-model="form.maritalStatus" placeholder="婚姻状态" clearable>
        <el-option label="已婚" value="0" />
        <el-option label="未婚" value="1" />
        <el-option label="其他" value="2" />
      </el-select>
    </el-form-item>
    <el-form-item label="政治面貌:">
      <el-input v-model="form.politicsStatus" placeholder="政治面貌" clearable />
    </el-form-item>
    <el-form-item label="宗教信仰:">
      <el-input v-model="form.religion" placeholder="宗教信仰" clearable />
    </el-form-item>
    <el-form-item label="星座:">
      <el-input v-model="form.constellation" placeholder="星座" clearable />
    </el-form-item>
    <el-form-item label="毕业学校:">
      <el-input v-model="form.school" placeholder="毕业学校" clearable />
    </el-form-item>
    <el-form-item label="学历:">
      <el-input v-model="form.degrees" placeholder="学历" clearable />
    </el-form-item>
    <el-form-item label="专业:">
      <el-input v-model="form.soecialty" placeholder="专业" clearable />
    </el-form-item>
    <el-form-item label="身份证号:">
      <el-input v-model="form.idCard" placeholder="身份证号" clearable />
    </el-form-item>
    <el-form-item label="手机号:">
      <el-input v-model="form.tel" placeholder="手机号" clearable />
    </el-form-item>
    <el-form-item label="家庭电话:">
      <el-input v-model="form.phone" placeholder="家庭电话" clearable />
    </el-form-item>
    <el-form-item label="身份证地址:">
      <el-input v-model="form.idCardAddress" placeholder="身份证地址" clearable />
    </el-form-item>
    <el-form-item label="现居住地:">
      <el-input v-model="form.nowAddress" placeholder="现居住地" clearable />
    </el-form-item>
    <el-form-item label="是否和前单位有纠纷:">
      <el-select v-model="form.ifDispute" placeholder="是否和前单位有纠纷" clearable>
        <el-option label="否" value="0" />
        <el-option label="是" value="1" />
      </el-select>
    </el-form-item>
    <el-form-item label="纠纷备注说明:">
      <el-input v-model="form.ifDisputeRemark" placeholder="纠纷备注说明" type="textarea" />
    </el-form-item>
    <el-form-item label="是否因工作或品行被解雇:">
      <el-select v-model="form.ifFire" placeholder="是否因工作或品行被解雇" clearable>
        <el-option label="否" value="0" />
        <el-option label="是" value="1" />
      </el-select>
    </el-form-item>
    <el-form-item label="解雇备注说明:">
      <el-input v-model="form.ifFireRemark" placeholder="解雇备注说明" type="textarea" />
    </el-form-item>
    <el-form-item label="是否有犯罪记录:">
      <el-select v-model="form.ifCrime" placeholder="是否有犯罪记录" clearable>
        <el-option label="否" value="0" />
        <el-option label="是" value="1" />
      </el-select>
    </el-form-item>
    <el-form-item label="犯罪备注说明:">
      <el-input v-model="form.ifCrimeRemark" placeholder="犯罪备注说明" type="textarea" />
    </el-form-item>

    <el-form-item label="是否接受新人三天离职薪资:">
      <el-select v-model="form.ifNoSalary" placeholder="是否接受新人三天离职薪资" clearable>
        <el-option label="否" value="0" />
        <el-option label="是" value="1" />
      </el-select>
    </el-form-item>
    <el-form-item label="是否接受单休:">
      <el-select v-model="form.ifSingleDayWeekend" placeholder="是否接受单休" clearable>
        <el-option label="否" value="0" />
        <el-option label="是" value="1" />
      </el-select>
    </el-form-item>
    <el-form-item label="是否接受加班:">
      <el-select v-model="form.ifWorkOvertime" placeholder="是否接受加班" clearable>
        <el-option label="否" value="0" />
        <el-option label="是" value="1" />
      </el-select>
    </el-form-item>
    <el-form-item label="目前工作状态:">
      <el-select v-model="form.workStatus" placeholder="目前工作状态" clearable>
        <el-option label="离职" value="0" />
        <el-option label="在职" value="1" />
        <el-option label="其他" value="2" />
      </el-select>
    </el-form-item>
    <el-form-item label="是否会驾驶:">
      <el-select v-model="form.ifDrive" placeholder="是否会驾驶" clearable>
        <el-option label="否" value="0" />
        <el-option label="是" value="1" />
      </el-select>
    </el-form-item>

    <el-form-item label="入职能提供的证明:">
      <el-checkbox-group v-model="form.certificate">
        <el-checkbox v-for="cert in availableCertificates" :key="cert.value" :value="cert.value" name="type">
          {{ cert.label }}
        </el-checkbox>
      </el-checkbox-group>
    </el-form-item>

    <el-form-item label="试用期薪资要求:">
      <el-input v-model="form.salary" placeholder="试用期薪资要求" clearable />
    </el-form-item>
    <el-form-item label="到岗时间:">
      <div class="demo-date-picker">
        <el-date-picker v-model="form.workingHours" type="date" placeholder="到岗时间" format="YYYY/MM/DD"
          value-format="YYYY-MM-DD">
          <template #default="cell">
            <div class="cell" :class="{ current: cell.isCurrent }">
              <span class="text">{{ cell.text }}</span>
              <span v-if="isHoliday(cell)" class="holiday" />
            </div>
          </template>
        </el-date-picker>
      </div>
    </el-form-item>

    <!-- 家庭成员信息 -->
    <el-form :inline="true" :model="form" class="demo-form-inline">
      <el-form-item v-for="(family, index) in form.employeeFamilyInformationFormList" :key="index">
        <div class="flex gap-2">
          <el-tag type="primary">
            家庭成员信息 {{ index + 1 }}
          </el-tag>
        </div>
        <el-form-item style="height: 120px;">
          <el-form-item label="家庭关系:">
            <el-input v-model="family.familyRelationships" placeholder="家庭关系" clearable />
          </el-form-item>
          <el-form-item label="姓名:">
            <el-input v-model="family.name" placeholder="姓名" clearable />
          </el-form-item>
          <el-form-item label="年龄:">
            <el-input v-model="family.age" placeholder="年龄" clearable />
          </el-form-item>
          <el-form-item label="电话:">
            <el-input v-model="family.tel" placeholder="电话" clearable />
          </el-form-item>
          <el-form-item label="职业:">
            <el-input v-model="family.occupation" placeholder="职业" clearable />
          </el-form-item>
          <el-form-item label="详细地址:">
            <el-input v-model="family.address" placeholder="详细地址" clearable />
          </el-form-item>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" :plain="true" @click="removeFamilyMember(index)">移除</el-button>
        </el-form-item>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" :plain="true" @click="addFamilyMember">添加家庭成员</el-button>
      </el-form-item>
    </el-form>

    <!-- 员工工作信息 -->
    <el-form :inline="true" :model="form" class="demo-form-inline">
      <el-form-item v-for="(work, index) in form.employeeWorkExperienceFormList" :key="index">
        <div class="flex gap-2">
          <el-tag type="primary">
            工作经历 {{ index + 1 }}
          </el-tag>
        </div>
        <el-form-item style="height: 180px;">
          <el-form-item label="工作时间:">
            <div class="demo-date-picker">
              <el-date-picker v-model="work.workTime" type="date" placeholder="工作时间" format="YYYY/MM/DD"
                value-format="YYYY-MM-DD">
                <template #default="cell">
                  <div class="cell" :class="{ current: cell.isCurrent }">
                    <span class="text">{{ cell.text }}</span>
                    <span v-if="isHoliday(cell)" class="holiday" />
                  </div>
                </template>
              </el-date-picker>
            </div>
          </el-form-item>
          <el-form-item label="工作单位名称:">
            <el-input v-model="work.workUnitName" placeholder="工作单位名称" clearable />
          </el-form-item>
          <el-form-item label="薪资:">
            <el-input v-model="work.salary" placeholder="薪资" clearable />
          </el-form-item>
          <el-form-item label="主管姓名:">
            <el-input v-model="work.supervisorName" placeholder="主管姓名" clearable />
          </el-form-item>
          <el-form-item label="主管手机号:">
            <el-input v-model="work.supervisorTel" placeholder="主管手机号" clearable />
          </el-form-item>
          <el-form-item label="离职时间和原因:">
            <el-input v-model="work.resignationTimeAndReason" placeholder="离职时间和原因" type="textarea"
              style="width: 220px" />
          </el-form-item>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" :plain="true" @click="removeWorkExperience(index)">移除</el-button>
        </el-form-item>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" :plain="true" @click="addWorkExperience">添加工作经历</el-button>
      </el-form-item>
    </el-form>

    <!-- 员工教育培训情况 -->
    <el-form :inline="true" :model="form" class="demo-form-inline">
      <el-form-item v-for="(education, index) in form.employeeEducationAndTrainingSituationTables" :key="index">
        <div class="flex gap-2">
          <el-tag type="primary">
            教育培训情况 {{ index + 1 }}
          </el-tag>
        </div>
        <el-form-item style="height: 120px;">
          <el-form-item label="学校、机构名称:">
            <el-input v-model="education.school" placeholder="学校、机构名称" clearable />
          </el-form-item>
          <el-form-item label="学历:">
            <el-input v-model="education.degrees" placeholder="学历" clearable />
          </el-form-item>
          <el-form-item label="毕业日期:">
            <div class="demo-date-picker">
              <el-date-picker v-model="education.graduationDate" type="date" placeholder="工作时间" format="YYYY/MM/DD"
                value-format="YYYY-MM-DD">
                <template #default="cell">
                  <div class="cell" :class="{ current: cell.isCurrent }">
                    <span class="text">{{ cell.text }}</span>
                    <span v-if="isHoliday(cell)" class="holiday" />
                  </div>
                </template>
              </el-date-picker>
            </div>
          </el-form-item>
          <el-form-item label="证书名称:">
            <el-input v-model="education.certName" placeholder="证书名称" clearable />
          </el-form-item>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" :plain="true" @click="removeEducation(index)">移除</el-button>
        </el-form-item>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" :plain="true" @click="addEducation">添加教育培训情况</el-button>
      </el-form-item>
    </el-form>

    <el-form-item style="padding-top: 20px;margin-left: 45%;">
      <el-button type="primary" :plain="true" @click="onSubmit">提交</el-button>
    </el-form-item>
  </el-form>
</template>

<script setup>
import { reactive } from 'vue';
import axios from 'axios';
import { ElMessage } from 'element-plus';

const holidays = [
  '2021-10-01',
  '2021-10-02',
  '2021-10-03',
  '2021-10-04',
  '2021-10-05',
  '2021-10-06',
  '2021-10-07',
]

const isHoliday = ({ dayjs }) => {
  return holidays.includes(dayjs.format('YYYY-MM-DD'))
}

const form = reactive({
  name: '',
  sex: '',
  bloodType: '',
  birthday: '',
  nation: '',
  height: '',
  weight: '',
  nativePlace: '',
  maritalStatus: '',
  politicsStatus: '',
  religion: '',
  constellation: '',
  school: '',
  degrees: '',
  soecialty: '',
  idCard: '',
  tel: '',
  phone: '',
  idCardAddress: '',
  nowAddress: '',
  ifDispute: '',
  ifDisputeRemark: '',
  ifFire: '',
  ifFireRemark: '',
  ifCrime: '',
  ifCrimeRemark: '',
  ifNoSalary: '',
  ifSingleDayWeekend: '',
  ifWorkOvertime: '',
  workStatus: '',
  ifDrive: '',
  certificate: [],
  salary: '',
  workingHours: '',
  employeeFamilyInformationFormList: [],
  employeeWorkExperienceFormList: [],
  employeeEducationAndTrainingSituationTables: []
});

const availableCertificates = [
  { value: '0', label: '身份证' },
  { value: '1', label: '毕业证' },
  { value: '2', label: '学位证' },
  { value: '3', label: '驾照' },
  { value: '4', label: '资格证' },
  { value: '5', label: '离职证明' },
  { value: '6', label: '其他' },
];

const addFamilyMember = () => {
  form.employeeFamilyInformationFormList.push({
    familyRelationships: '',
    name: '',
    age: '',
    tel: '',
    occupation: '',
    address: ''
  });
};

const removeFamilyMember = (index) => {
  form.employeeFamilyInformationFormList.splice(index, 1);
};

const addWorkExperience = () => {
  form.employeeWorkExperienceFormList.push({
    workTime: [],
    workUnitName: '',
    salary: '',
    supervisorName: '',
    supervisorTel: '',
    resignationTimeAndReason: ''
  });
};

const removeWorkExperience = (index) => {
  form.employeeWorkExperienceFormList.splice(index, 1);
};

const addEducation = () => {
  form.employeeEducationAndTrainingSituationTables.push({
    school: '',
    degrees: '',
    graduationDate: [],
    certName: ''
  });
};

const removeEducation = (index) => {
  form.employeeEducationAndTrainingSituationTables.splice(index, 1);
};

const onSubmit = async () => {
  const data = {
    ...form,
    certificate: form.certificate.join(','),
  };
  try {
    const response = await axios.post('/api/employeeRecruitmentRegistrationForm/add', data);
    ElMessage({
      message: '提交成功',
      type: 'success',
    })
    console.log('Response:', response.data);
  } catch (error) {
    ElMessage.error('提交失败')
    console.error('Error:', error);
  }
}
</script>

<style scoped>
.demo-form-inline {
  max-width: 100%;
  padding: 20px;
  margin-top: 26px;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  background-color: #fff;
}

.demo-form-inline .el-input {
  --el-input-width: 220px;
}

.demo-form-inline .el-select {
  --el-select-width: 220px;
}

.cell {
  height: 30px;
  padding: 3px 0;
  box-sizing: border-box;
}

.cell .text {
  width: 24px;
  height: 24px;
  display: block;
  margin: 0 auto;
  line-height: 24px;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 50%;
}

.cell.current .text {
  background: #626aef;
  color: #fff;
}

.cell .holiday {
  position: absolute;
  width: 6px;
  height: 6px;
  background: var(--el-color-danger);
  border-radius: 50%;
  bottom: 0px;
  left: 50%;
  transform: translateX(-50%);
}

.gap-2 {
  margin-right: 20px;
}
</style>