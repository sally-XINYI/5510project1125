<template>
    <div>
        <head-top></head-top>
        <el-row style="margin-top: 20px;">
            <el-col :span="12" :offset="4">
                <el-form :model="repaymentForm" :rules="rules" ref="formData" label-width="110px" class="demo-formData">
                    <el-row>
                        <el-col :span="12">
                            <el-form-item label="Remain Repayment Amount" prop="remainrepaymentamount">
                                <el-input v-model="repaymentForm.remainrepaymentamount"></el-input>
                            </el-form-item>
                        </el-col>
                        <el-col :span="12">
                            <el-form-item label="Remaining Installments" prop="remaininginstallments">
                                <el-input v-model.number="repaymentForm.remaininginstallments"></el-input>
                            </el-form-item>
                        </el-col>
                    </el-row>
                    <el-row>
                        <el-col :span="12">
                            <el-form-item label="Next Repayment Amount" prop="nextrepaymentamount">
                                <el-input v-model.number="repaymentForm.nextrepaymentamount"></el-input>
                            </el-form-item>
                        </el-col>
                        <el-col :span="12">
                            <el-form-item label="Next Repayment Date" prop="nextrepaymentdate">
                                <el-input v-model.number="repaymentForm.nextrepaymentdate"></el-input>
                            </el-form-item>
                        </el-col>
                    </el-row>
                    <el-form-item label="Repayment Amount" prop="repaymentamount">
                        <el-input v-model.number="repaymentForm.repaymentamount"></el-input>
                    </el-form-item>
                </el-form>
                <el-button @click="onSubmit" type="primary">Submit</el-button>
            </el-col>
        </el-row>
    </div>
</template>

<script>
    import headTop from '@/components/headTop'
    import {getRepyament} from '@/api/getData'
    import {baseUrl, baseImgPath} from '@/config/env'
    export default {
        data(){
            return {
                repaymentForm: {
                    remainrepaymentamount: '',
                    remaininginstallments: '',
                    nextrepaymentamount: '',
                    nextrepaymentdate: '',
                    repaymentamount: ''
                }
            }
        },
        components: {
            headTop,
        },
        mounted(){
            this.initData();
        },
        methods: {
            submitcategoryForm(repaymentForm) {
                this.$refs[repaymentForm].validate(async (valid) => {
                    if (valid) {
                        const params = {
                        }
                        try{
                            const result = await addCategory(params);
                            if (result.status == 1) {
                                this.initData();
                                this.categoryForm.name = '';
                                this.categoryForm.description = '';
                                this.showAddCategory = false;
                                this.$message({
                                    type: 'success',
                                    message: '添加成功'
                                });
                            }
                        }catch(err){
                            console.log(err)
                        }
                    } else {
                        this.$notify.error({
                            title: '错误',
                            message: '请检查输入是否正确',
                            offset: 100
                        });
                        return false;
                    }
                });
            },
            onSubmit(){
                if (this.$router.query.repaymentamount != this.$router.query.remainrepaymentamount){
                    this.$alert('Error', 'miaomiaomiao', {
                        confirmButtonText: 'Confirm',
                        callback: action => {
                            this.$message({
                                type: 'info',
                                message: `action: ${action}`
                            });
                        }
                    })
                }
                else{
                    this.$alert('Success', 'LOAN...', {
                        confirmButtonText: 'Confirm',
                        callback: action => {
                            this.$message({
                                type: 'info',
                                message: `action: ${action}`
                            });
                        }
                    });
                }
            }
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
