<script setup>
// 在 Vue3 CompositionAPI 中
// 1. 获取路由对象 router  useRouter
//    const router = useRouter()
// 2. 获取路由参数 route   useRoute
//    const route = useRoute()
import { useRoute, useRouter } from 'vue-router'
import { useUserStore, useCountStore } from '@/stores'
const router = useRouter()
const route = useRoute()

const goList = () => {
  router.push('/list')
  console.log(router, route)
}
const userStore = useUserStore()
const countStore = useCountStore()
</script>

<template>
  <hr />
  <router-view></router-view>
  <hr />

  <div>我是App</div>
  <!-- 全局组件创建了就可以直接使用 -->
  <test-demo />
  <el-button @click="$router.push('/home')">跳首页</el-button>
  <el-button @click="goList">跳列表页</el-button>

  <p>{{ userStore.token }}</p>
  <el-button @click="userStore.setToken('Bearer sidfhheiwhuvyweqrjh')">
    登录
  </el-button>
  <el-button @click="userStore.removeToken()">退出</el-button>

  <hr />
  {{ countStore.count }}
  <el-button @click="countStore.add(2)">加法2</el-button>
</template>

<style scoped></style>
