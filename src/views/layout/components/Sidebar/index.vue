<!-- 导航菜单 -->
<template>
    <el-scrollbar wrap-class="scrollbar-wrapper">
        <!--
            show-timeout 展开延时
            collapse: 是否水平折叠收起菜单
        -->
        <el-menu
            :show-timeout="200"
            :default-active="$route.path"
            mode="vertical"
            :collapse="isCollpse"
            background-color="#304156"
            text-color="#bfcbd9"
            active-text-color="#409EFF"
        >
            <!-- ！！！bug -->
            <sidebar-item v-for="route in permission_routes" :item="route" :base-path="route.path" :key="route.path"/>
            <!-- <div class="menu-wrapper" v-for="route in routes" :key="route.path">
              <el-menu-item :index="route">{{route.path}}</el-menu-item>
            </div> -->
        </el-menu>
    </el-scrollbar>
</template>
<script>
import SidebarItem from './sidebarItem'
import {mapGetters} from 'vuex'
export default {
  data () {
    return {
      isUnique: true
    }
  },
  created() {
    console.log(1)
    console.log(this.permission_routes)
  },
  computed: {
    ...mapGetters([
      'sidebar',
      'permission_routes'
    ]),
    // 获取路由表
    routes () {
      return this.$router.options.routes
    },
    isCollpse () {
      return this.sidebar.opened
    }
  },
  components: {
    SidebarItem
  }
}
</script>
