<template>
    <div class="main">
        <div class="login">
            <div class="logo">
                <img class='img' src="@/assets/logo.png" alt="logo">
            </div>
            <el-form :model="user" label-width="auto" style="max-width: 600px" class="user_form" :rules="userRules" ref="userFormRef">
                <el-form-item label="用户名" prop="name">
                    <el-input v-model="user.name" placeholder="请输入用户名" :prefix-icon="User"/>
                </el-form-item>
                    <el-form-item label="密码" prop="pwd">
                    <el-input v-model="user.pwd" placeholder="请输入密码" :prefix-icon="Lock" show-password/>
                </el-form-item>
                <el-form-item class="btns">
                    <el-button type="primary" @click="onSubmit">登录</el-button>
                    <el-button type="success" @click="resetForm(userFormRef)">重置密码</el-button>
                </el-form-item>
            </el-form>
                    
        </div>
    </div>
</template>


<script setup>
import { reactive,ref } from 'vue'
import {User,Lock} from '@element-plus/icons-vue'
const user = reactive({
    name: '',
    pwd: ''
})

const userRules = {
    name: [
        { required: true, message: '用户名不能为空', trigger: 'blur' },
        { min: 3, max: 10, message: '用户名长度在3-10个字符之间', trigger: 'blur' }
    ],
    pwd: [
        { required: true, message: '密码不能为空', trigger: 'blur' }
    ]
}

const userFormRef = ref(null)
const resetForm = (formRef) =>
{
    formRef.resetFields()
}


</script>


<style scoped>
    .main {
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #f5f5f5;
        /* border: 1px solid black; */
    }
    .login {
        width: 450px;
        height: 300px;
        background-color: white;
        border-radius: 10px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);

    }
    .logo{
        width: 50px;
        height: 50px;
        /* border: 1px solid black; */
        margin: 0 auto;
        overflow: hidden;
        position: relative;
        left: 5%;
        transform: translateX(-50%);
        top: 30px;
    }
    .img{
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
    .user_form{
        padding: 50px;
        padding-top: 70px;
    }
    .btns{
        display: flex;
        justify-content: space-between;
    }
    .btns button{
        flex: 1;
    }

</style>