<template>
  <div class="navbar">
    <hamburger :is-active="sidebar.opened" class="hamburger-container" @toggleClick="toggleSideBar" />
    <!-- 下拉菜单 -->
    <div class="right-menu">
      <img class="user-avatar">
      <el-dropdown class="avatar-container" trigger="click">
        <i class="el-icon-setting" />
        <el-dropdown-menu slot="dropdown" class="user-dropdown">
          <router-link to="/">
          </router-link>
          <a target="_blank" href="#">
            <el-dropdown-item>百度</el-dropdown-item>
          </a>
          <el-dropdown-item>
            <span style="display:block;">退出</span>
          </el-dropdown-item>
        </el-dropdown-menu>
      </el-dropdown>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import Hamburger from '@/components/Hamburger'

export default {
  components: {
    Hamburger
  },
  computed: {
    ...mapGetters([
      'sidebar'
    ])
  },
  methods: {
    toggleSideBar() {
      this.$store.dispatch('app/toggleSideBar')
    }
  }
}
</script>

<style lang="scss" scoped>
.navbar {
  height: 50px;
  overflow: hidden;
  position: relative;
  background: #fff;
  box-shadow: 0 1px 4px rgba(0, 21, 41, .08);

  .hamburger-container {
    line-height: 46px;
    height: 100%;
    float: left;
    cursor: pointer;
    transition: background .3s;
    -webkit-tap-highlight-color: transparent;

    &:hover {
      background: rgba(0, 0, 0, .025)
    }
  }

  .breadcrumb-container {
    float: left;
  }

  .right-menu {
    float: right;
    height: 100%;
    line-height: 50px;
    margin-right: 25px;

    // 动态头像
    .user-avatar {
      width: 50px;
      height: 50px;
      border-radius: 5px;
    }

    &:focus {
      outline: none;
    }


    .avatar-container {
      margin-right: 30px;
      height: 100%;
      line-height: 100%;
      position: relative;

      .el-icon-setting {
        cursor: pointer;
        position: absolute;
        top: 10px;
        right: -40px;
        font-size: 30px;
      }
    }


  }
}
</style>
