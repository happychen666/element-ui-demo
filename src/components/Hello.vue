<template>
  <div class="hello">
    <div @click="dakaiEvent">dakaiEvent</div>
    <div @click="guanbiEvent">guanbiEvent</div>
    <el-row class="tac">
      <el-col :span="12">
        <el-menu
          class="el-menu-vertical-demo"
          :unique-opened="true"
          @open="handleOpen"
          ref="menu"
        >
          <el-submenu :index="menuData.index">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>{{ menuData.navTitle.name }}{{ menuData.index }}</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">选项1</el-menu-item>
              <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group>
              <el-menu-item index="1-3">选项3</el-menu-item>
              <el-menu-item index="1-3">选项4</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
        </el-menu>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: "hello",
  props: {
    indexData: {
      required: true,
      default: "0",
    },
    menuData: {
      required: true,
      default: () => ({}),
    },
  },
  data() {
    return {
      menuComonent: [],
    };
  },
  mounted() {
    this.menuComonent = this.$parent.$children;
    // console.log(this.$parent.$children[0].dakaiEvent());
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log("indexData===>", this.indexData);
      console.log("handleOpen");
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log("handleClose");
      console.log(key, keyPath);
    },
    dakaiEvent() {
      this.$refs.menu.open(this.menuData.index);

      const menus = this.menuComonent;
      for (let index = 0; index < menus.length; index++) {
        const element = menus[index];
        if (element.indexData !== this.indexData) {
          console.log("0000", element);
          element.guanbiEvent();
        }
      }
    },
    guanbiEvent() {
      this.$refs.menu.close(this.menuData.index);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
