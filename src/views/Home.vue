<template>
  <div class="home">
    <el-row>
      <el-col :span="12">
        <img src="@/assets/logo.png" alt="View's logo " />
      </el-col>
      <el-col :span="12">
        <div class="grid-content bg-purple-light">
          <h2>{{Greeting}}</h2>
        </div>
        <div class="grid-content bg-purple-light">{{VueDesc}}</div>
      </el-col>
    </el-row>
  </div>
</template>
<script>
export default {
  data() {
    return {
      Greeting: "Welcome to My Vue App",
      VueDesc:
        "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum"
    };
  }
};
</script>
<style>
src {
  width: 100px;
}
</style>