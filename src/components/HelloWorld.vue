<template>
  <div class="pagation">
    <h1>分页样式</h1>
    <div class="table-main">
      <div class="search">
        <el-input v-model="searchData" placeholder="Search Tenants" class="input"></el-input>
        <el-button slot="append" icon="el-icon-search" type="primary"></el-button>
      </div>
      <el-table :data="tableData" border>
        <el-table-column prop="username" label="User Name" align="center"></el-table-column>
        <el-table-column prop="userDescription" label="User Description" align="center"></el-table-column>
        <el-table-column prop="userEmail" label="User Email" align="center"></el-table-column>
        <el-table-column prop="userPhoneNumber" label="User Phone Number" align="center"></el-table-column>
        <el-table-column prop="userLocation" label="User Location" align="center"></el-table-column>
        <el-table-column prop="userCompany" label="usesr.colUserCompany" align="center"></el-table-column>
        <el-table-column label="Actions" align="center">
          <el-button size="mini" type="primary">Edit</el-button>
          <el-button size="mini" type="danger">Delete</el-button>
        </el-table-column>
      </el-table>
      <div class="pagination">
        <el-pagination
          background
          layout="total, sizes, prev, pager, next, jumper, slot"
          @current-change="handleCurrentChange"
          @size-change="handleSizeChange"
          :current-page="currentPage"
          :page-size="pageSize"
          :total="total"
        ></el-pagination>
      </div>
    </div>
  </div>
</template>

<script>
import Mock from "mockjs";

export default {
  name: "HelloWorld",
  data: function() {
    return {
      Mock: Mock,
      tableData: [
        {
          username: "username",
          userDescription: "User Description",
          userEmail: "User Email",
          userPhoneNumber: "User Phone Number",
          userLocation: "User Location",
          userCompany: "usesr.colUserCompany"
        }
      ],
      total: 10,
      pageSize: 10,
      searchData: "",
      currentPage: 1,
      dataList: []
    };
  },

  computed: {},

  created: function() {
    let Random = Mock.Random;
    Random.date();
    let dataMock = Mock.mock({
      "dataList|50": [
        {
          username: "@cname",
          userDescription: "@cname",
          userEmail: "@email",
          "userPhoneNumber|1000001-200000": 123456,
          userLocation: "@cname",
          userCompany: "@csentence"
        }
      ]
    });

    this.dataList = dataMock.dataList;
    this.total = this.dataList.length;
    this.tableData = this.dataList.slice(0, this.pageSize);
  },

  methods: {
    handleCurrentChange: function(val) {
      this.currentPage = val;
      this.tableData = this.dataList.slice(
        (val - 1) * this.pageSize,
        this.pageSize * val
      );
    },

    handleSizeChange: function(val) {
      this.pageSize = val;
      this.tableData = this.dataList.slice(
        this.currentPage - 1,
        val * this.currentPage
      );
    }
  }
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.pagination {
  float: left;
  margin-top: 50px;
}

.search {
  float: left;
  margin-bottom: 20px;
}

.input {
  width: 200px;
  margin-right: 10px;
}
</style>
