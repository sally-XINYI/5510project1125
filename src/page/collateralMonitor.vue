<template>
    <div>
        <head-top></head-top>
        <el-row style="margin-top: 20px;">
            <el-row :gutter="20">
                <el-col :span="3" style="margin-left: 20px">
                    <el-button @click="authenticate" type="primary">Authenticate</el-button>
                </el-col>
                <el-col :span="3">
                    <el-upload
                        class="upload-demo"
                        action="https://jsonplaceholder.typicode.com/posts/"
                        :on-preview="handlePreview"
                        :on-remove="handleRemove"
                        :before-remove="beforeRemove"
                        multiple
                        :limit="3"
                        :on-exceed="handleExceed"
                        :file-list="fileList">
                        <el-button type="primary">Upload Asset</el-button>
                    </el-upload>
                </el-col>
            </el-row>
            <el-table
                :data="tableData"
                stripe
                style="width: 100%; margin-top: 30px">
                <el-table-column
                    prop="digitalsignature"
                    label="Digital Signature"
                    width="180">
                </el-table-column>
                <el-table-column
                    prop="collateraltype"
                    label="Clooateral Type"
                    width="180">
                </el-table-column>
                <el-table-column
                    prop="valueatloan"
                    label="Value at loan"
                    width="180">
                </el-table-column>
                <el-table-column
                    prop="presentvalue"
                    label="Present Value"
                    width="180">
                </el-table-column>
                <el-table-column
                    prop="collateralstatus"
                    label="Collateral Status">
                </el-table-column>
            </el-table>
        </el-row>
    </div>
</template>

<script>
    import headTop from '@/components/headTop'
    // import {cityGuess, addShop, searchplace, foodCategory} from '@/api/getData'
    // import {baseUrl, baseImgPath} from '@/config/env'
    export default {
        data() {
            return {
                tableData: [{
                    digitalsignature: '',
                    collateraltype: '',
                    valueatloan: '',
                    presentvalue: '',
                    collateralstatus: '',
                }, {
                    digitalsignature: '',
                    collateraltype: '',
                    valueatloan: '',
                    presentvalue: '',
                    collateralstatus: '',
                }, {
                    digitalsignature: '',
                    collateraltype: '',
                    valueatloan: '',
                    presentvalue: '',
                    collateralstatus: '',
                }],
            }
        },
        components: {
            headTop,
        },
        methods :{
            errorHandler(){
                return true
            },
            authenticate(){
                this.$router.push('mainPage')
            }},
        mounted() {
            this.initData();
        }
    }
</script>

<style lang="less">
    @import '../style/mixin';
    .button_submit{
        text-align: center;
    }
    .avatar-uploader .el-upload {
        border: 1px dashed #d9d9d9;
        border-radius: 6px;
        cursor: pointer;
        position: relative;
        overflow: hidden;
    }
    .avatar-uploader .el-upload:hover {
        border-color: #20a0ff;
    }
    .avatar-uploader-icon {
        font-size: 28px;
        color: #8c939d;
        width: 120px;
        height: 120px;
        line-height: 120px;
        text-align: center;
    }
    .avatar {
        width: 120px;
        height: 120px;
        display: block;
    }
    .el-table .info-row {
        background: #c9e5f5;
    }

    .el-table .positive-row {
        background: #e2f0e4;
    }
</style>
