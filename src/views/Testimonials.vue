<template>
  <div class="testimonials">
    <h1>Testimonials</h1>
  <ul>
    <li v-for="(testimonial, index) in testimonials" :key="index" @click="testimonials(index)">
      {{ testimonials }}
    </li>
  </ul>
    
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

import axios from 'axios'

export default {

  props: {
    testimonials: {
      type: Array,
      required: true
    },
  },
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
  },
  addTestimonial(testimonials) {
      this.testimonials.push(testimonials);
      axios
        .put(
          "https://midterm-testimonials.firebaseio.com/data.json",
          this.testimonials
        )
        
        // arrow function => replaces the regular function syntax
        .then(response => {
          console.log(response);
          console.log("Your data was saved status: " + response.status);
        }) //if the put is successfull then "then" will run if not "catch" will run
        .catch(error => {
          console.log(error);
        });
    },
created() {
    axios
      .get("https://midterm-testimonials.firebaseio.com/data.json")
      .then(response => {
        console.log(response.data);
        if (response.data) {
          this.testimonials = response.data;
        }
      })
      .catch(error => {
        console.log("There was an error in getting data: " + error.response);
      });
  }
};
</script>
