<template>
    <div>
      <h1>{{ title }}</h1>
  
      <label>Name : </label>
      <input class="name" type="text" placeholder="Enter name" v-model="name"/><br /><br />
      <label>Age : </label>
      <input type="text" placeholder="Enter age" v-model="age" /><br /><br />
      <label>Email : </label>
      <input type="gmail" placeholder="Enter email" v-model="email" /><br /><br />
  
      <input type="radio" value="Male" v-model="gender" />
      <label> Male</label>
      <input type="radio" value="Female" v-model="gender" />
      <label> Female</label><br /><br />
  
      <textarea rows="3" cols="50" v-model="about"></textarea><br /><br />
  
      <button @click.prevent="submitted()">Submit</button><br /><br />
  
      <table>
        <tr>
          <th>Name</th>
          <th>Age</th>
          <th>Email</th>
          <th>Gender</th>
          <th>About</th>
        </tr>
        <tr v-for="(info, index) in infos" :key="index">
          <td>{{ info.name }}</td>
          <td>{{ info.age }}</td>
          <td>{{ info.email }}</td>
          <td>{{ info.gender }}</td>
          <td>{{ info.about }}</td>
          <td>
            <button @click="deleteItem(index)">Delete</button>
            <button>Edit</button>
          </td>
        </tr>
      </table>
    </div>
  </template>
  <script>
  export default {
    name: "App",
  
    data() {
      return {
        title: "Hello Puja",
        name: "",
        age: "",
        email: "",
        gender: "",
        about: "",
        infos: [],
      };
    },
    methods: {
      getTimeOfDay() {
        const now = new Date();
        const hours = now.getHours();
  
        if (hours >= 5 && hours < 12) {
          return "Morning";
        } else if (hours >= 12 && hours < 18) {
          return "Evening";
        } else {
          return "Night";
        }
      },
  
      submitted() {
        if (
          this.name == "" ||
          this.age == "" ||
          this.email == "" ||
          this.gender == "" ||
          this.about == ""
        ) {
          alert("Please fill the form");
          return;
        }
        let infoData = {
          name: this.name,
          age: this.age,
          email: this.email,
          gender: this.gender,
          about: this.about,
        };
        this.infos.push(infoData);
        this.name = "";
        this.age = "";
        this.email = "";
        this.gender = "";
        this.about = "";
      },
  
      deleteItem(index) {
        this.infos = this.infos.filter((infos, toIndex) => toIndex !== index);
      },
    },
    mounted() {
      // $(document).ready(function () {
      //   console.log($(".name").val());
      // });
    },
  
    created() {
      this.title = this.title + " , " + this.getTimeOfDay();
      let data = [
        {
          name: "nitesh", 
          age: "24",
          email: "nipu@gmail.com",
          gender: "Male",
          about: "hi",
        },
        {
          name: "puja",
          age: "24",
          email: "nipu@gmail.com",
          gender: "Male",
          about: "hi",
        },
      ];
      this.infos = data;
    },
  };
  </script>
  
  <style>
  table,
  th,
  td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  </style>
  