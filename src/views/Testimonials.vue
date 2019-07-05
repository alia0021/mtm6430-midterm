<template>
  <el-row type="flex" justify="center">
    <el-col :span="14">
      <el-row :gutter="20">
        <el-col :sm="12" v-for="(ruleForm, index) in ruleForms" :key="index">
          <el-card class="box-card" :sm="12">
            <div slot="header" class="clearfix">
              <span>{{ ruleForm.YourName }} - {{ ruleForm.PositionTitle }}</span>
            </div>
            <div class="text item">{{ ruleForm.Comment }}</div>
          </el-card>
        </el-col>
      </el-row>
      <el-row class="form-row">
        <el-col :sm="12" :offset="6">
          <el-form
            label-position="top"
            label-width="100px"
            :model="ruleForm"
            :rules="rules"
            ref="ruleForm"
          >
            <el-row :gutter="10">
              <el-col :sm="12">
                <el-form-item label="Your Name" prop="YourName">
                  <el-input v-model="ruleForm.YourName"></el-input>
                </el-form-item>
              </el-col>
              <el-col :sm="12">
                <el-form-item label="Position Title" prop="PositionTitle">
                  <el-input v-model="ruleForm.PositionTitle"></el-input>
                </el-form-item>
              </el-col>
              <el-col :span="24">
                <el-form-item label="Your Comments" prop="Comment">
                  <el-input type="textarea" v-model="ruleForm.Comment"></el-input>
                </el-form-item>
                <el-form-item>
                  <el-button type="primary" @click="submitForm('ruleForm')">Submit</el-button>
                </el-form-item>
              </el-col>
            </el-row>
          </el-form>
        </el-col>
      </el-row>
    </el-col>
  </el-row>
</template> 
<script>
import axios from "axios";

export default {
  data() {
    return {
      Title: "Testimonials",
      Subtitle: "Leave us your Testimonials",
      // add my dialog info
      dialogVisible: false,
      ruleForms: null,
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
            min: 0,
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
          console.log("valid form");
          axios
            .post(
              "https://midterm-testimonials.firebaseio.com/midterm.json",
              this.ruleForm
            )
            .then(response => {
              console.log(response.status);
              this.ruleForm.YourName = "";
              this.ruleForm.PositionTitle = "";
              this.ruleForm.Comment = "";
              axios
                .get("https://midterm-testimonials.firebaseio.com/midterm.json")
                .then(response => {
                  this.ruleForms = response.data;
                })
                .catch(error => {
                  console.log(error.response);
                });
            })
            .catch(error => {
              console.log(error.response);
            });
        } else {
          console.log("invalid");
          return false;
        }
      });
    }
  },
  created() {
    axios
      .get("https://midterm-testimonials.firebaseio.com/midterm.json")
      .then(response => {
        this.ruleForms = response.data;
      })
      .catch(error => {
        console.log("There was an error in getting data: " + error.response);
      });
  }
};
</script>
<style>
.text {
  font-size: 14px;
}

.item {
  padding: 18px 0;
}

.box-card {
  width: 480px;
}
</style>
