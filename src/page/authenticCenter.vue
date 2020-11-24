<template>
    <div>
        <head-top></head-top>
        <el-row style="margin-top: 20px;">
            <el-row :gutter="20">
                <el-col :span="8" style="margin-left: 100px">
                    Business Registration No.<el-input v-model="input1"></el-input>
                </el-col>
                <el-col :span="8" style="margin-left: 50px">
                    Enterprise Name<el-input v-model="input2"></el-input>
                </el-col>
            </el-row>
            <el-tabs v-model="activeName" type="card" @tab-click="handleClick" style="margin-top: 30px">
                <el-tab-pane label="Real Estate" name="first">
                    <el-table
                        ref="multipleTable"
                        :data="realEstateData"
                        tooltip-effect="dark"
                        style="width: 100%"
                        @selection-change="handleSelectionChange">
                        <el-table-column
                            type="selection"
                            width="55">
                        </el-table-column>
                        <el-table-column
                            prop="enterprise"
                            label="Enterprise ID"
                            width="180">
                        </el-table-column>
                        <el-table-column
                            prop="id"
                            label="ID"
                            width="100">
                        </el-table-column>
                        <el-table-column
                            prop="name"
                            label="Name"
                            width="100">
                        </el-table-column>
                        <el-table-column
                            prop="nature"
                            label="Nature"
                            width="100">
                        </el-table-column>
                        <el-table-column
                            prop="purchase_price"
                            label="Purchase Price"
                            width="180">
                        </el-table-column>
                        <el-table-column
                            prop="address"
                            label="Address"
                            width="120">
                        </el-table-column>
                        <el-table-column
                            prop="purchase_date"
                            label="Purchase Date"
                            width="180">
                        </el-table-column>
                        <el-table-column
                            prop="Status"
                            label="Status"
                            show-overflow-tooltip>
                        </el-table-column>
                    </el-table>
                </el-tab-pane>
                <el-tab-pane label="deposit" name="second">
                    <el-table
                        ref="multipleTable"
                        :data="depositData"
                        tooltip-effect="dark"
                        style="width: 100%"
                        @selection-change="handleSelectionChange">
                        <el-table-column
                            type="selection"
                            width="55">
                        </el-table-column>
                        <el-table-column
                            prop="enterprise"
                            label="Enterprise ID"
                            width="180">
                        </el-table-column>
                        <el-table-column
                            prop="id"
                            label="ID"
                            width="100">
                        </el-table-column>
                        <el-table-column
                            prop="bank"
                            label="Bank"
                            width="100">
                        </el-table-column>
                        <el-table-column
                            prop="name"
                            label="Name"
                            width="80">
                        </el-table-column>
                        <el-table-column
                            prop="account"
                            label="Account"
                            width="100">
                        </el-table-column>
                        <el-table-column
                            prop="amount"
                            label="Amount"
                            width="100">
                        </el-table-column>
                        <el-table-column
                            prop="deposit_date"
                            label="Deposit Date"
                            width="150">
                        </el-table-column>
                        <el-table-column
                            prop="expiration_date"
                            label="Expiration Date"
                            width="150">
                        </el-table-column>
                        <el-table-column
                            prop="Status"
                            label="Status"
                            show-overflow-tooltip>
                        </el-table-column>
                    </el-table>
                </el-tab-pane>
                <el-tab-pane label="receivables" name="third">
                    <el-table
                        ref="multipleTable"
                        :data="receivabelsData"
                        tooltip-effect="dark"
                        style="width: 100%"
                        @selection-change="handleSelectionChange">
                        <el-table-column
                            type="selection"
                            width="55">
                        </el-table-column>
                        <el-table-column
                            prop="enterprise"
                            label="Enterprise ID"
                            width="180">
                        </el-table-column>
                        <el-table-column
                            prop="id"
                            label="ID"
                            width="100">
                        </el-table-column>
                        <el-table-column
                            prop="payer_name"
                            label="Payer Name"
                            width="80">
                        </el-table-column>
                        <el-table-column
                            prop="payer_industry"
                            label="Payer Industry"
                            width="150">
                        </el-table-column>
                        <el-table-column
                            prop="payer_nature"
                            label="Payer Nature"
                            width="80">
                        </el-table-column>
                        <el-table-column
                            prop="payee_name"
                            label="Payee Name"
                            width="80">
                        </el-table-column>
                        <el-table-column
                            prop="amount"
                            label="Amount"
                            width="100">
                        </el-table-column>
                        <el-table-column
                            prop="invoice_date"
                            label="Invoice Date"
                            width="80">
                        </el-table-column>
                        <el-table-column
                            prop="payment_due"
                            label="Payment Due"
                            width="90">
                        </el-table-column>
                        <el-table-column
                            prop="Status"
                            label="Status"
                            show-overflow-tooltip>
                        </el-table-column>
                    </el-table>
                </el-tab-pane>
                <div style="margin-top: 30px">
                    <el-button @click="authenticate">Authenticate</el-button>
                </div>
            </el-tabs>
        </el-row>
    </div>
</template>

<script>
    import headTop from '@/components/headTop'
    import {getRealEstateList, getDepositList, getReceivablesList} from '@/api/getData'
    export default {
        data() {
            return {
                realEstateData: [{
                    enterprise: '1',
                    id: '1',
                    name: '1',
                    nature: '1',
                    purchase_price: '1',
                    address: '1',
                    purchase_date: '1',
                    Status: '1'
                },{
                    enterprise: '1',
                    id: '1',
                    name: '1',
                    nature: '1',
                    purchase_price: '1',
                    address: '1',
                    purchase_date: '1',
                    Status: '1'
                },{
                    enterprise: '1',
                    id: '1',
                    name: '1',
                    nature: '1',
                    purchase_price: '1',
                    address: '1',
                    purchase_date: '1',
                    Status: '1'
                }],
                depositData:[{
                    enterprise: '2',
                    id: '2',
                    bank: '2',
                    name: '2',
                    account: '2',
                    amount: '2',
                    deposit_date: '2',
                    expiration_date: '2',
                    Status: '2'
                }],
                receivabelsData: [{
                    enterprise: '3',
                    id: '3',
                    payer_name: '3',
                    payer_industry: '3',
                    payer_nature: '3',
                    payee_name: '3',
                    amount: '3',
                    invoice_date: '3',
                    payment_due: '3',
                    Status: '3'
                }],
                activeName:'first',
                input1: '',
                input2: ''
            }
        },
        components: {
            headTop,
        },
        methods :{
            handleClick(tab, event) {
                console.log(tab, event);
            },
            errorHandler(){
                return true
            },
            // async getRealEstate(){
            //     const realEstate = await getRealEstateList({offset: this.offset, limit: this.limit});
            //     this.relaEstateData = [];
            //     realEstate.forEach(item => {
            //         const realEstateData = {};
            //         tableData.username = item.username;
            //         tableData.registe_time = item.registe_time;
            //         tableData.city = item.city;
            //         this.tableData.push(tableData);
            //     })
            // }
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
    .el-table{
        font-size: 10px;
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
