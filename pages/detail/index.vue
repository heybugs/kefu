<template>
  <div class="container">
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
    <el-row :gutter="20" style="padding:20px 40px">
      <el-col :span="6" style="min-width: 200px;">
        <el-form ref="form" :model="form" label-width="80px" label-position="right" size="mini">
          <el-form-item label="客户头像">
            <el-avatar src="/img/user.jpg"></el-avatar>
          </el-form-item>
          <el-form-item label="客户昵称">
            <el-input style="width:180px" v-model="form.nick_name"></el-input>
          </el-form-item>
          <el-form-item label="真实姓名">
            <el-input style="width:180px" v-model="form.real_name"></el-input>
          </el-form-item>
          <el-form-item label="客户状态">
            <el-input style="width:180px" v-model="form.status"></el-input>
          </el-form-item>
          <el-form-item label="来源">
            <el-input style="width:180px" v-model="form.form"></el-input>
          </el-form-item>
          <el-form-item label="客户等级">
            <el-select style="width:180px" v-model="form.user_level" placeholder="">
              <el-option label="普通用户" value="普通用户"></el-option>
              <el-option label="VIP" value="VIP"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item label="电话">
            <el-input style="width:180px" v-model="form.phone"></el-input>
          </el-form-item>
          <el-form-item label="邮箱">
            <el-input style="width:180px" v-model="form.email"></el-input>
          </el-form-item>
          <el-form-item label="城市">
            <el-select style="width:180px" v-model="form.city" placeholder="请选择城市">
              <el-option label="北京" value="北京"></el-option>
              <el-option label="上海" value="上海"></el-option>
              <el-option label="天津" value="天津"></el-option>
              <el-option label="广州" value="广州"></el-option>
              <el-option label="石家庄" value="石家庄"></el-option>
              <el-option label="秦皇岛" value="秦皇岛"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item label="备注">
            <el-input style="width:180px" type="textarea" v-model="form.note"></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="onSubmit">保存</el-button>
            <el-button>取消</el-button>
          </el-form-item>
        </el-form>
      </el-col>
      <el-col :span="18" style="min-width: 800px;">
        <p style="font-size:18px">联络记录</p>
        <div v-for="item in calledList" :key="item.id">
          <div style="margin:20px 0;"><span style="font-size:16px;">呼叫</span> {{item.call_date}}</div>
          <el-row :gutter="20" style="margin: 20px 0;font-size:14px">
            <el-col :span="4">所属业务：--</el-col>
            <el-col :span="4">业务类型：--</el-col>
            <el-col :span="4">处理状态：--</el-col>
            <el-col :span="4">备注说明：--</el-col>
          </el-row>
          <el-table :data="item.tableData" style="width: 100%">
            <el-table-column prop="kefu_name" label="客服" width="120"></el-table-column>
            <el-table-column prop="call_phone" label="主叫号码">
            </el-table-column>
            <el-table-column prop="called_phone" label="被叫号码">
            </el-table-column>
            <el-table-column width="120" prop="call_status" label="接听状态">
              <template slot-scope="scope">
                <el-tag v-if="scope.row.call_status !==1" type="success">已接听</el-tag>
                <el-tag v-else type="danger">未接听</el-tag>
              </template>
            </el-table-column>
            <el-table-column width="120" prop="call_type" label="呼叫类型">
            </el-table-column>
            <el-table-column width="120" prop="call_time" label="通话总时长">
            </el-table-column>
            <el-table-column width="120" prop="call_address" label="对方归属地">
            </el-table-column>
          </el-table>
          <!-- <el-row style="margin: 20px 0;">
            <el-col>

            </el-col>
          </el-row> -->

        </div>
      </el-col>
    </el-row>

  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: "",
        region: "",
        date1: "",
        date2: "",
        delivery: false,
        type: [],
        resource: "",
        desc: "",
      },
      calledList: [
        {
          id: 1,
          call_date: "2022-09-11 18:09:12",
          tableData: [
            {
              kefu_name: "王小虎",
              call_phone: "18030263296",
              called_phone: "12345678910", //随机数
              call_status: 1, // 已接听1 未接听2 默认0
              call_type: "呼出",
              call_time: "00:01:34", // 随机数
              call_address: "上海",
            },
          ],
        },

        {
          id: 2,
          call_date: "2022-09-11 18:09:22",
          tableData: [
            {
              kefu_name: "张三",
              call_phone: "18030263296",
              called_phone: "", //随机数
              call_status: 1, // 已接听1 未接听2 默认0
              call_type: "呼出",
              call_time: "00:01:34", // 随机数
              call_address: "上海",
            },
          ],
        },
        {
          id: 3,
          call_date: "2022-09-11 18:09:22",
          tableData: [
            {
              kefu_name: "张三",
              call_phone: "18030263296",
              called_phone: "", //随机数
              call_status: 1, // 已接听1 未接听2 默认0
              call_type: "呼出",
              call_time: "00:01:34", // 随机数
              call_address: "上海",
            },
          ],
        },
      ],
    };
  },
  methods: {
    onSubmit() {
      console.log("submit!");
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

