<template>
    <div>
        <head-top></head-top>
        <el-row style="margin-top: 20px;">
            <el-col :span="12" :offset="4">
                <el-form :model="formData" :rules="rules" ref="formData" label-width="110px" class="demo-formData">
                    <el-form-item label="Business Registration No." prop="businessregistration">
                        <el-input v-model="formData.businessregistration"></el-input>
                    </el-form-item>
                    <el-form-item label="Enterprise Name" prop="enterprisename">
                        <el-input v-model.number="formData.enterprisename"></el-input>
                    </el-form-item>
                    <el-form-item label="Loan Amount" prop="loanamount">
                        <el-input v-model="formData.loanamount"></el-input>
                    </el-form-item>
                    <el-form-item label="Period">
                        <el-select v-model="value" placeholder="Please select">
                            <el-option
                                v-for="item in options"
                                :key="item.value"
                                :label="item.label"
                                :value="item.value">
                            </el-option>
                        </el-select>
                    </el-form-item>
                    <el-form-item label="Repayment Type">
                        <el-select v-model="value1" placeholder="Please select">
                            <el-option
                                v-for="item in options1"
                                :key="item.value1"
                                :label="item.label1"
                                :value="item.value1">
                            </el-option>
                        </el-select>
                    </el-form-item>
                </el-form>
                <el-row>
                    <el-col :span="12">
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
                    <el-col :span="12">
                        <el-button @click="onSubmit" type="primary">Submit</el-button>
                    </el-col>
                </el-row>
            </el-col>
        </el-row>
    </div>
</template>

<script>
    import headTop from '@/components/headTop'
    import {cityGuess, addShop, searchplace, foodCategory} from '@/api/getData'
    import {baseUrl, baseImgPath} from '@/config/env'
    export default {
        data(){
            return {
                city: {},
                formData: {
                    name: '', //店铺名称
                    address: '', //地址
                    latitude: '',
                    longitude: '',
                    description: '', //介绍
                    phone: '',
                    promotion_info: '',
                    float_delivery_fee: 5, //运费
                    float_minimum_order_amount: 20, //起价
                    is_premium: true,
                    delivery_mode: true,
                    new: true,
                    bao: true,
                    zhun: true,
                    piao: true,
                    startTime: '',
                    endTime: '',
                    image_path: '',
                    business_license_image: '',
                    catering_service_license_image: '',

                },
                rules: {
                    name: [
                        {required: true, message: '请输入店铺名称', trigger: 'blur'},
                    ],
                    address: [
                        {required: true, message: '请输入详细地址', trigger: 'blur'}
                    ],
                    phone: [
                        {required: true, message: '请输入联系电话'},
                        {type: 'number', message: '电话号码必须是数字'}
                    ],
                },
                options: [{
                    value: '7 days',
                    label: '7 days'
                }, {
                    value: '14 days',
                    label: '14 days'
                }, {
                    value: '30 days',
                    label: '30 days'
                }, {
                    value: '60 days',
                    label: '60 days'
                }, {
                    value: '90 days',
                    label: '90 days'
                }, {
                    value: '180 days',
                    label: '180 days'
                }, {
                    value: '270 days',
                    label: '270 days'
                }, {
                    value: '1 year',
                    label: '1 year'
                }, {
                    value: '2 years',
                    label: '2 years'
                }, {
                    value: '3 years',
                    label: '3 years'
                }, {
                    value: '4 years',
                    label: '4 years'
                }, {
                    value: '5 years',
                    label: '5 years'
                }],
                value:'',
                options1: [{
                    value1: 'Lump Sum',
                    label1: 'Lump Sum'
                }, {
                    value1: 'Equal principal payment',
                    label1: 'Equal principal payment'
                }, {
                    value1: 'Equal loan payment',
                    label1: 'Equal loan payment'
                }],
                value1:''
            }
        },
        components: {
            headTop,
        },
        methods: {
            onSubmit(){
                this.$alert('Your application has been received the loan amount is !', 'Success', {
                    confirmButtonText: 'Confirm',
                    callback: action => {
                        this.$message({
                            type: 'info',
                            message: `action: ${action}`
                        });
                    }
                });
            }
        },
        mounted(){
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
