<template>
    <div>
        <head-top></head-top>
        <el-row style="margin-top: 20px;">
            <el-col :span="12" :offset="4">
                <div class="left" width="80%">
                    <el-form :model="formData" :rules="rules" ref="formData" label-width="110px" class="demo-formData">
                        <el-form-item label-width="200px" label="Business Registration No." prop="businessregistration">
                            <el-input v-modeL="formData.businessregistration"></el-input>
                        </el-form-item>
                        <el-form-item label-width="200px" label="Enterprise Name" prop="enterprisename">
                            <el-input v-modeL="formData.enterprisename"></el-input>
                        </el-form-item>
                        <el-form-item label-width="200px" label="Establish Date" prop="establishdate">
                            <el-input v-modeL="formData.establishdate"></el-input>
                        </el-form-item>
                        <el-form-item label-width="200px" label="Enterprise Nature" prop="enterprisenature">
                            <el-input v-modeL="formData.establishdate"></el-input>
                        </el-form-item>
                    </el-form>
                </div>
                <div class="right" width="15%">
                    <div class="demo-type">
                        <el-avatar :size="60" src="https://empty" @error="errorHandler">
                            <img :src="squareUrl"/>
                        </el-avatar>
                    </div>
                </div>
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
                formData: {
                    businessregistration: '',
                    enterprisename: '',
                    estabishdate: '',
                    enterprisenature:''
                },
                // rules: {
                //     businessregistration: [
                //         { required: true, message: 'Please Input Business Registration.', trigger: 'blur' },
                //     ],
                //     enterprisename: [
                //         { required: true, message: 'Please Input Enterprise Name.', trigger: 'blur' }
                //     ],
                //     collateralprice: [
                //         { required: true, message: 'Please Input Collateral Price.' },
                //         { type: 'number', message: 'Collateral Price must be number.' }
                //     ],
                // },
            }
        },
        components: {
            headTop,
        },
        methods :{
            errorHandler(){
                return true
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
