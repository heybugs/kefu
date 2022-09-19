<template>
  <div>
    <el-container>
      <el-header>Header</el-header>
      <el-container>
        <el-aside width="60px">
          <el-menu default-active="1" class="el-menu-vertical-demo" background-color="#545c64" text-color="#fff" active-text-color="#ffd04b">
            <el-menu-item index="1">
              <i class="el-icon-location"></i>
            </el-menu-item>
            <el-menu-item index="2">
              <i class="el-icon-menu"></i>
              <span slot="title"></span>
            </el-menu-item>
            <el-menu-item index="3">
              <i class="el-icon-document"></i>
              <span slot="title"></span>
            </el-menu-item>
            <el-menu-item index="4">
              <i class="el-icon-setting"></i>
              <span slot="title"></span>
            </el-menu-item>
          </el-menu>
        </el-aside>
        <el-main>
          <el-tabs v-model="activeName">
            <el-tab-pane label="客户" name="first">
              <el-table :data="tableData">
                <el-table-column prop="nick_name" label="客户昵称" width="120">
                </el-table-column>
                <el-table-column prop="real_name" label="真实姓名" width="120">
                </el-table-column>
                <el-table-column prop="company" label="公司" width="140">
                </el-table-column>
                <el-table-column prop="user_level" label="客户等级" width="140">
                </el-table-column>
                <el-table-column prop="vip_level" label="VIP级别" width="140">
                </el-table-column>
                <el-table-column prop="email" label="邮箱" width="140">
                </el-table-column>
                <el-table-column prop="creat_date" label="创建日期" width="140">
                </el-table-column>
                <el-table-column prop="update_date" label="更新日期" width="140">
                </el-table-column>
                <el-table-column prop="action" label="操作">
                  <template slot-scope="scope">
                    <el-button @click="detailClick(scope.row)" type="text" size="small">查看详情</el-button>
                    <el-button type="text" size="small" @click="deleteClick(scope.row)">删除</el-button>
                  </template>

                </el-table-column>
              </el-table>
              <el-pagination @size-change="handleSizeChange" @current-change="handleCurrentChange" :current-page="currentPage" :page-sizes="[10, 20, 30, 40,50]" :page-size="10" layout="total, sizes, prev, pager, next, jumper" :total="40">
              </el-pagination>
            </el-tab-pane>
            <el-tab-pane label="黑名单(0)" name="second">暂无数据</el-tab-pane>
          </el-tabs>

        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
const item = {
  id: 1,
  nick_name: "未知用户",
  real_name: "王女士",
  company: "--",
  user_level: "普通客户",
  vip_level: "--",
  email: "--",
  creat_date: "2022-09-12",
  update_date: "2022-09-12",
};
export default {
  name: "IndexPage",
  data() {
    return {
      activeName: "first",
      tableData: Array(20).fill(item),
      currentPage: 1,
    };
  },
  methods: {
    detailClick(id) {
      console.log(id);
    },
    deleteClick(id) {
      this.$message.error("您的账号暂无权限删除！");
    },
    handleSizeChange(val) {
        console.log(`每页 ${val} 条`);
      },
      handleCurrentChange(val) {
        console.log(`当前页: ${val}`);
      }
  },
};
</script>

<style>
.el-header {
  background-color: #b3c0d1;
  color: #333;
  text-align: center;
  line-height: 60px;
}
</style>
