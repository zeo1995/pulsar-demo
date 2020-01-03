<template>
  	<div class="pagation">
    	<h1>分页样式</h1>
    	<div class="table-main">
     		<el-table :data="tableData" border >
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
                    :page-size="pageSize"
                    :total="total">
                </el-pagination>
            </div>
    	</div>
  	</div>
</template>

<script>
export default {
	name: "HelloWorld",
	data: function() {
		return {
			tableData: [
				{
					username: 'username',
					userDescription: 'User Description',
					userEmail: 'User Email',
					userPhoneNumber: 'User Phone Number',
					userLocation: 'User Location',
					userCompany: 'usesr.colUserCompany'
				}
            ],
            total: 10,
            pageSize: 10
		}
    },

    computed: {
        
    },

    created: function() {
        
    },

    methods: {
        getData: function() {
            this.$axios.get( ).then(res => {
                
                
            });

        },
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
</style>
