<template>
  <div id="nav">
    <nav>
      <el-menu
        :default-active="activeIndex2"
        class="el-menu-demo"
        mode="horizontal"
        @select="handleSelect"
        background-color="#777"
        text-color="black"
        font-size="1.4em"
        active-text-color="#ffd04b"
      >
        <el-menu-item>
          <h1>My Vue App</h1>
        </el-menu-item>
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
    </nav>
    <footer>{{Copyright}}</footer>
  </div>
</template>
<script>
export default {
  data() {
    return {
      Copyright: "Copyright, MIT Open lincence."
    };
  }
};
</script>            
<style>
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
