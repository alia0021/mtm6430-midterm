<template>
  <div id="nav">
    <el-container>
      <el-header>
        <h1>{{NameofWebsite}}</h1>
      </el-header>
      <el-menu
        :default-active="activeIndex2"
        class="el-menu-demo"
        mode="horizontal"
        @select="handleSelect"
        background-color="#b3c0d1"
        text-color="black"
        font-size="1.4em"
        active-text-color="#ffd04b"
      >
        <el-menu-item index="1">
          <router-link :to="{ name: 'home' }">Home</router-link>
        </el-menu-item>
        <el-menu-item index="2">
          <router-link :to="{ name: 'about' }">About</router-link>
        </el-menu-item>
        <el-menu-item index="3">
          <router-link :to="{ name: 'contact' }">Contact</router-link>
        </el-menu-item>
        <el-menu-item index="4">
          <router-link :to="{ name: 'testimonials' }">Testimonials</router-link>
        </el-menu-item>
      </el-menu>

      <el-footer>{{Copyright}}</el-footer>
    </el-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      NameofWebsite: "My Vue App",
      Copyright: "Copyright, MIT Open lincence.",
      activeIndex: "1",
      activeIndex2: "1"
    };
  },
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
    }
  }
};
</script>            
<style>
.el-header,
.el-footer,
.el-menu {
  background-color: #b3c0d1;
  color: #333;
  text-align: center;
  line-height: 60px;
}

nav {
  padding: 0px;
  bottom: 20px;
}
footer {
  background-color: #777;
  padding: 30px;
  color: white;
  position: absolute;
  bottom: 30px;
  margin: auto;
  width: 100%;
  font-size: 1.2rem;
  text-align: right;
}
</style>
