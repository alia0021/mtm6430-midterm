<template>
  <div class="about">
    <h1>{{header}}</h1>
    <img src="@/assets/logo.png" alt="View's logo " />
 <el-col :span="20" 
        <div class="grid-content bg-purple-light">{{ParagraphOne}}</div>
      </el-col>
    </el-row>
       </el-row>
      <el-col :span="24">
        <div class="grid-content bg-purple-light">{{ParagraphOne}}</div>
      </el-col>
    </el-row>
      <img src="@/assets/logo.png" alt="View's logo " />
  </div>
</template>         
<script>
export default {
  data() {
    return {
      header: "About the Vue app",
      ParagraphOne:
        "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum"
    };
  }
};
</script>            
<style>
h2 {
  color: #0dee89;
}
</style>
