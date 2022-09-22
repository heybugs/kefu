<template>
  <div>
    <el-container>
      <el-header id="header">
        <el-image style="height: 41px;width:46px" src="/img/logo.png"></el-image>
        <div class="right">
          <div class="box" style="width:120px">
            <el-image style="height: 40px;width:40px;" src="/img/banner-logo-3.png"></el-image>
            <p>客服工作台</p>
          </div>
          <div class="box">
            <el-avatar src="/img/avatar38.png"></el-avatar>
            <el-dropdown>
              <span class="el-dropdown-link">
                <span class="w-font">王梅</span><i class="el-icon-arrow-down el-icon--right"></i>
              </span>
              <el-dropdown-menu slot="dropdown">
                <el-dropdown-item>退出</el-dropdown-item>
              </el-dropdown-menu>
            </el-dropdown>
          </div>
        </div>
      </el-header>
      <el-container>
        <el-aside width="60px" style="background: #33435b;">
          <el-menu default-active="1" class="el-menu-vertical-demo" background-color="#33435b" text-color="#fff" active-text-color="#ffd04b">
            <el-menu-item index="1">
              <i class="el-icon-house"></i>
            </el-menu-item>
            <el-menu-item index="2">
              <i class="el-icon-user"></i>
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
    detailClick(item) {
      console.log(item);
      // this.$router.push({
      //   path: `/detail?id=${item.id}`,
      // });
      let routeInfo = this.$router.resolve({ path: `/detail?id=${item.id}` });
      window.open(routeInfo.href, "_blank");
    },
    deleteClick(id) {
      this.$message.error("您的账号暂无权限删除！");
    },
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
    },
  },
};
</script>

<style>
body {
  margin: 0;
  color: #909399;
}
.el-header {
  background-color: #09aeb0;
  color: #333;
  text-align: center;
  line-height: 60px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.right {
  display: flex;
  align-items: center;
  width: 240px;
  justify-content: space-between;
}
.box {
  display: flex;
  align-items: center;
  width: 100px;
  justify-content: space-between;
  font-size: 14px;
}
</style>
