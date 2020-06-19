<template>
    <div class="index" >
        <div style="text-align: center">
            <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
                <el-menu-item index="1">处理中心</el-menu-item>
                <el-submenu index="2">
                    <template slot="title">我的工作台</template>
                    <el-menu-item index="2-1">选项1</el-menu-item>
                    <el-menu-item index="2-2">选项2</el-menu-item>
                    <el-menu-item index="2-3">选项3</el-menu-item>
                    <el-submenu index="2-4">
                        <template slot="title">选项4</template>
                        <el-menu-item index="2-4-1">选项1</el-menu-item>
                        <el-menu-item index="2-4-2">选项2</el-menu-item>
                        <el-menu-item index="2-4-3">选项3</el-menu-item>
                    </el-submenu>
                </el-submenu>
                <el-menu-item index="3" >消息中心</el-menu-item>
                <el-menu-item index="4">订单管理</el-menu-item>
            </el-menu>
            <div class="line">
                <div id="line1" v-if="isShow">
                    <el-table
                            :data="tableData"
                            border
                            style="width: 100%">
                        <el-table-column
                                fixed
                                prop="date"
                                label="日期"
                                width="150">
                        </el-table-column>
                        <el-table-column
                                prop="name"
                                label="姓名"
                                width="120">
                        </el-table-column>
                        <el-table-column
                                prop="province"
                                label="省份"
                                width="120">
                        </el-table-column>
                        <el-table-column
                                prop="city"
                                label="市区"
                                width="120">
                        </el-table-column>
                        <el-table-column
                                prop="address"
                                label="地址"
                                width="300">
                        </el-table-column>
                        <el-table-column
                                prop="zip"
                                label="邮编"
                                width="120">
                        </el-table-column>
                        <el-table-column
                                fixed="right"
                                label="操作"
                                width="100">
                            <template slot-scope="scope">
                                <el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button>
                                <el-button type="text" size="small">编辑</el-button>
                            </template>
                        </el-table-column>
                    </el-table>
                </div>


                <div id="line2">
                    <div class="block" v-if="isShow02">
                        <el-timeline>
                            <el-timeline-item timestamp="2018/4/12" placement="top">
                                <el-card>
                                    <h4>更新 Github 模板</h4>
                                    <p>王小虎 提交于 2018/4/12 20:46</p>
                                </el-card>
                            </el-timeline-item>
                            <el-timeline-item timestamp="2018/4/3" placement="top">
                                <el-card>
                                    <h4>更新 Github 模板</h4>
                                    <p>王小虎 提交于 2018/4/3 20:46</p>
                                </el-card>
                            </el-timeline-item>
                            <el-timeline-item timestamp="2018/4/2" placement="top">
                                <el-card>
                                    <h4>更新 Github 模板</h4>
                                    <p>王小虎 提交于 2018/4/2 20:46</p>
                                </el-card>
                            </el-timeline-item>
                        </el-timeline>
                    </div>
                </div>

            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                activeIndex: '1',
                isShow: true,
                isShow02: false,
                tableData: [{
                    date: '2016-05-02',
                    name: '王小虎',
                    province: '上海',
                    city: '普陀区',
                    address: '上海市普陀区金沙江路 1518 弄',
                    zip: 200333
                }, {
                    date: '2016-05-04',
                    name: '王小虎',
                    province: '上海',
                    city: '普陀区',
                    address: '上海市普陀区金沙江路 1517 弄',
                    zip: 200333
                }, {
                    date: '2016-05-01',
                    name: '王小虎',
                    province: '上海',
                    city: '普陀区',
                    address: '上海市普陀区金沙江路 1519 弄',
                    zip: 200333
                }, {
                    date: '2016-05-03',
                    name: '王小虎',
                    province: '上海',
                    city: '普陀区',
                    address: '上海市普陀区金沙江路 1516 弄',
                    zip: 200333
                }]
            };
        },
        methods: {
            handleSelect(key, keyPath) {
                let _this = this;
                console.log(key, keyPath);
                if(key==3){
                    this.isShow = !this.isShow;
                    this.isShow02 = !this.isShow02;
                    // _this.$router.push('/Message');
                }
                if(key==1){
                    this.isShow02 = !this.isShow02;
                    this.isShow = !this.isShow;
                }
                if(key==4){
                    let _this = this;
                    _this.$router.push('/Message');
                }
            },
            handleClick(row) {
                console.log(row);
            }
        }
    }
</script>

<style scoped>

</style>