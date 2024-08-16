<script setup>
import { RouterLink, RouterView } from 'vue-router';
</script>

<template>
  <div class="flex gap-2">
    <RouterLink to="/">
      <el-tag type="primary">
        新增员工应聘登记信息
      </el-tag>
    </RouterLink>
    <RouterLink to="/about">
      <el-tag type="primary">
        查询员工应聘登记信息
      </el-tag>
    </RouterLink>
  </div>

  <RouterView />
</template>

<style scoped>
.gap-2{
  height: 10px;
}

a {
  text-align: center;
  color: #333;
  font-weight: 700;
  text-decoration: none;
  margin-left: 20px;
}
</style>
