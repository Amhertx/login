<template>
    <div id="app">
        <el-card class="box">
            <span>登录</span>

            <div class="text item">
                <el-form :inline="true" v-model="user" class="demo-form-inline">
                    <el-form-item label="邮箱">
                        <el-input v-model="loginForm.userName" placeholder="请输入邮箱"></el-input>
                    </el-form-item>
                    <br>
                    <el-form-item label="密码">
                        <el-input v-model="loginForm.password" type="password" placeholder="请输入密码"></el-input>
                    </el-form-item>
                    <br>
                    <el-form-item>
                        <el-button type="primary" @click="submit">登录</el-button>
                    </el-form-item>
                </el-form>
            </div>

        </el-card>
    </div>
</template>

<script>
    import axios from 'axios'

    export default {
        name: "login",
        data() {
            return {
                loginForm: {
                    userName: "",
                    password: ""
                }
            }
        },
        methods: {
            submit() {
                axios
                    .post('/goLogin', {
                        params: {
                            loginForm: this.loginForm
                        }
                    })
                    .then(function (code) {
                        console.log(code);
                        this.$message('登录成功！');
                    })
                    .catch(function (error) {
                        console.log(error);
                        this.$message('请求异常！');
                    });


            }


        }
    }
</script>

<style>

    .el-card__body {
        padding: 20px;
        background-color: #ff782f;
    }

    .el-button {
        width: 206px;

        margin-left: 38px;
    }

    .text {
        font-size: 14px;
    }

    .item {
        margin-bottom: 18px;
    }

    .clearfix:before,
    .clearfix:after {
        display: table;
        content: "";
    }

    .clearfix:after {
        clear: both
    }

    .box {
        width: 480px;
    }
</style>