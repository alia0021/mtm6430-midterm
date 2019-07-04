<template>
  <div class="testimonials">
    <h1>Testimonials</h1>
    <!--v-show will only show my form if my dialogvisible is false -->
    <el-form
      v-show="!dialogVisible"
      :model="ruleForm"
      :rules="rules"
      ref="ruleForm"
      label-width="220px"
      class="demo-ruleForm"
    >
      <h3>Leave us a Testimonial</h3>
      <el-form-item label="Your Name" prop="YourName">
        <!-- input First name and property -->
        <el-input placeholder="Name here" v-model="ruleForm.YourName"></el-input>
      </el-form-item>
      <el-form-item label="Position Title" prop="PositionTitle">
        <!-- input Last name and property -->
        <el-input   placeholder="Position Title" v-model="ruleForm.PositionTitle"></el-input>
      </el-form-item>
      <el-form-item label="Comment" prop="Comment">
        <el-input
          type="textarea"
          placeholder="Your Comment here."
          v-model="ruleForm.Comment"
        ></el-input>
      </el-form-item>
      </el-form-item>
      <el-form-item>
        <el-button @click="submitForm('ruleForm')">Submit</el-button>
      </el-form-item>
    </el-form>
  </div>
</template> 
<script>
export default {
  data() {
    return {
      // add my dialog info
      dialogVisible: false,
      // add my list of information
      ruleForm: {
        YourName: "",
        PositionTitle: "",
        Comment: ""
      },
      rules: {
        // add my rules for my data
        YourName: [
          {
            required: true,
            message: "Please input your Name",
            trigger: "blur"
          },
          {
            min: 0,
            max: 50,
            message: "Length should not be more than 50 characters",
            trigger: "blur"
          }
        ],
        PositionTitle: [
          {
            required: true,
            message: "Please input your Position Title",
            trigger: "blur"
          },
          {
            min: 5,
            max: 50,
            message: "Length should not be more than 50 characters",
            trigger: "blur"
          }
        ],
        
        Comment: [
          {
            required: true,
            message: "Please input your comment",
            trigger: "blur"
          },
              {
            min: 5,
            max: 120,
            message: "Length should not be more than 50 characters",
            trigger: "blur"
          }
        ]
      }
    };
  },
  methods: {
    // input my validations for my inputs and data
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          this.dialogVisible = true;
        } else {
          this.dialogVisible = false;
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
};
</script>
