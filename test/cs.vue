<template>
    <el-row>
        <el-col :span="24"><div class="user-top">
    <h3 class="title">用户管理</h3></div></el-col>
    <el-row>
    <el-row>
        <el-col :span="8">
            <el-tree :data="data" :props="defaultProps" @node-click="handleNodeClick"></el-tree></el-col>
        <el-col :span="16">
        <el-col :span="24" class="subtitle">红河信息技术部</el-col>
        <el-col :span="12">
            <el-input placeholder="请输入内容" v-model="input5" class="input-with-select">
                <el-button slot="append" icon="el-icon-search">查询</el-button>
            </el-input>
        </el-col>
            <el-col :span="12">
                <el-button type="text" @click="open5">批量导入</el-button>
            </el-col>
            <el-col :span="24">
                <el-table
                    ref="multipleTable"
                    :data="tableData3"
                    tooltip-effect="dark"
                    style="width: 100%"
                    @selection-change="handleSelectionChange">
                    <el-table-column
                    type="selection"
                    width="55">
                    </el-table-column>
                    <el-table-column
                    label="账号"
                    width="120">
                    <template slot-scope="scope">{{ scope.row.date }}</template>
                    </el-table-column>
                    <el-table-column
                    prop="name"
                    label="姓名"
                    width="120">
                    </el-table-column>
                    <el-table-column
                    prop="address"
                    label="分部"
                    show-overflow-tooltip>
                    </el-table-column>
                    <el-table-column
                    prop="address"
                    label="部门"
                    show-overflow-tooltip>
                    </el-table-column>
                    <el-table-column
                    prop="address"
                    label="锁定状态"
                    show-overflow-tooltip>
                    </el-table-column>
                    <el-table-column
                    prop="address"
                    label="启用状态"
                    show-overflow-tooltip>
                    </el-table-column>
                    <el-table-column
                    prop="address"
                    label="安全级别"
                    show-overflow-tooltip>
                    </el-table-column>
                </el-table>
            </el-col>
        </el-col>
            <el-col :span="24" class="toright">
                <el-pagination
                background
                layout="prev, pager, next"
                :total="1000">
                </el-pagination>
            </el-col>
        </el-row>
    </el-row>



    <!-- <el-row>
        <el-col :span="24">
            <div class="grid-content bg-purple-dark">
                <el-tree :data="data" :props="defaultProps" @node-click="handleNodeClick"></el-tree>
            </div></el-col>
    </el-row> -->
    </el-row>
</template>
<script>
import request from '@/utils/request'
export default {
    data() {
      return {
        data: [{
          label: '洪合科技-信息部',
          children: [{
            label: '红河科技信息部',
            children: [{
              label: '三级'
            }]
          },
          {
              label:'蓝河技术',
          },
          {
              label:'蓝河技术233',
          },
          {
              label:'蓝河技术666',
          }]
        }, {
          label: '一级 2',
          children: [{
            label: '二级 2-1',
            children: [{
              label: '三级 2-1-1'
            }]
          }, {
            label: '二级 2-2',
            children: [{
              label: '三级 2-2-1'
            }]
          }]
        }, {
          label: '一级 3',
          children: [{
            label: '二级 3-1',
            children: [{
              label: '三级 3-1-1'
            }]
          }, {
            label: '二级 3-2',
            children: [{
              label: '三级 3-2-1'
            }]
          }]
        }],
        defaultProps: {
          children: 'children',
          label: 'label'
        }
      };
    },
    methods: {
      handleNodeClick(data) {
        console.log(data);
      },
      toggleSelection(rows) {
        if (rows) {
          rows.forEach(row => {
            this.$refs.multipleTable.toggleRowSelection(row);
          });
        } else {
          this.$refs.multipleTable.clearSelection();
        }
      },
      handleSelectionChange(val) {
        this.multipleSelection = val;
      },
      open5() {
        this.$alert('<strong>这是 <i>HTML</i> 片段</strong>', 'HTML 片段', {
          dangerouslyUseHTMLString: true
        });
      }
    }
  };
</script>
<style scrped>
.user-top{
    color: #797979;
    background-color: #fafafa;
}
.user-top .title{
    font-size: 14px;
    text-transform: uppercase;
    font-weight: 600;
    margin-bottom: 0;
    margin-top: 0;
    color: inherit;
    line-height: 30px;
    margin:10px 30px 0;

}
.subtitle{
    margin: 20px;
    margin-left:0;
}
.toright{
    display: flex;
    justify-content: flex-end;
}
</style>

