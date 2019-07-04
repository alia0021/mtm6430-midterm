<template>
  <div class="contact">
    <h1>{{Contact}}</h1>
    <h3>Address{{Address}}</h3>
    <ul>
      Hours of Operations
      <li v-for="item of HoursofOp">{{item.name }} : {{ item.value }}</li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      Contact: "Contact",
      Address: " 2042 Frankinville Cres Mainville, ON V4D 7S8",
      HoursofOp: [
        {
          name: "Monday",
          value: "8AM-9PM"
        },
        {
          name: "Tuesday",
          value: "8AM-9PM"
        },
        {
          name: "Wednesday",
          value: "8AM-9PM"
        },
        {
          name: "Thursday",
          value: "8AM-9PM"
        },
        {
          name: "Friday",
          value: "8AM-9PM"
        },
        {
          name: "Saturday",
          value: "8AM-9PM"
        },
        {
          name: "Sunday",
          value: "8AM-9PM"
        }
      ]
    };
  }
};
</script>            