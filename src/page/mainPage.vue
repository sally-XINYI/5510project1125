<template>
    <div>
        <head-top></head-top>
        <el-row style="margin-top: 20px;">
            <el-col :span="12" :offset="4">
                <el-row :gutter="50">
                    <el-col :span="18">
                        <el-form :model="enterpriseData" :rules="rules" ref="formData" label-width="110px" class="demo-formData">
                            <el-form-item label-width="200px" label="Name" prop="name">
                                <el-input v-modeL="enterpriseData.name"></el-input>
                            </el-form-item>
                            <el-form-item label-width="200px" label="Credict Code" prop="credict_code">
                                <el-input v-modeL="enterpriseData.crdict_code"></el-input>
                            </el-form-item>
                            <el-form-item label-width="200px" label="Legal Person" prop="legal_person">
                                <el-input v-modeL="enterpriseData.legal_person"></el-input>
                            </el-form-item>
                            <el-form-item label-width="200px" label="Registration Time" prop="reg_time">
                                <el-input v-modeL="enterpriseData.reg_time"></el-input>
                            </el-form-item>
                            <el-form-item label-width="200px" label="Registration Capital" prop="reg_capital">
                                <el-input v-modeL="enterpriseData.reg_capital"></el-input>
                            </el-form-item>
                            <el-form-item label-width="200px" label="Registration Address" prop="reg_addr">
                                <el-input v-modeL="enterpriseData.reg_addr"></el-input>
                            </el-form-item>
                            <el-form-item label-width="200px" label="Industry" prop="industry">
                                <el-input v-modeL="enterpriseData.industry"></el-input>
                            </el-form-item>
                        </el-form>
                    </el-col>
                    <el-col :span="6" style="margin-top: 150px">
                        <div class="demo-type" @click="collateralMonitor">
                            <p>Remain Repayment Amount</p>
                        </div>
                    </el-col>
                </el-row>
                <el-row style="margin-top: 20px">
                    <el-col :span="8">
                        <el-button type="primary" @click="authentic">Authentic Center</el-button>
                    </el-col>
                    <el-col :span="8">
                        <el-button type="primary" @click="loanapplication">Loan Application</el-button>
                    </el-col>
                    <el-col :span="8">
                        <el-button type="primary" @click="repayment">Repayment</el-button>
                    </el-col>
                </el-row>
            </el-col>
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
                squareUrl: "https://cube.elemecdn.com/9/c2/f0ee8a3c7c9638a54940382568c9dpng.png",
                // sizeList: ["large", "medium", "small"],
                enterpriseData: {
                    name: '',
                    credict_code: '',
                    legal_person: '',
                    reg_time: '',
                    reg_capital: '',
                    reg_addr: '',
                    industry: ''
                }
            }
        },
        components: {
            headTop,
        },
        methods :{
            errorHandler(){
                return true
            },
            authentic(){
                this.$router.push('authenticCenter')
            },
            loanapplication(){
                this.$router.push('loanApplication')
            },
            repayment(){
                this.$router.push('repayment')
            },
            collateralMonitor(){
                this.$router.push('collateralMonitor')
            }
        },
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
