<template>
  <h1>Instakilo</h1>
  <form @submit.prevent="handleSubmit">
    <label>Email:</label>
    <input type="email" required v-model="email" />
    <label>Password:</label>
    <input type="password" required v-model="password" />
    <div v-if="passwordError" class="error">
      {{ passwordError }}
    </div>
    <label>Phone:</label>
    <input type="phone" required v-model="phone" />
    <div v-if="phoneError" class="error">
      {{ phoneError }}
    </div>
    <!-- <label>Role:</label>
    <select v-model="role">
      <option value="dveloper">Web Dveloper</option>
      <option value="designer">Web Designer</option>
    </select> -->
    <label>Hobies:</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>
    <div class="terms">
      <input type="checkbox" v-model="terms" required />
      <label>Accept terms and conditions</label>
    </div>

    <div class="submit">
      <button>Create an account</button>
    </div>
  </form>
  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Phone: {{ phone }}</p>
  <!-- <p>Role: {{ role }}</p> -->
  <p>Terms: {{ terms }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      phone: "",
      // role: "",
      terms: false,
      tempSkill: "",
      skills: [],
      passwordError: "",
      phoneError: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key == "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }
        this.tempSkill = "";
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item;
      });
    },
    handleSubmit() {
      // console.log("from Submitted");
      // check vlidate password
      this.passwordError =
        this.password.length > 5
          ? ""
          : "Password must be at least 6 chars long";
      this.phoneError =
        this.phone.length > 10 ? "" : "Phone No must be 11 chars long";
      if (!this.passwordError) {
        console.log("email: ", this.email);
        console.log("password: ", this.password);
        console.log("phone: ", this.phone);
        console.log("role: ", this.role);
        console.log("skills: ", this.skills);
        console.log("terms accepted: ", this.terms);
      }
    },
  },
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 20px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0;
  position: relative;
  top: 2px;
}
.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}
button {
  background: #0b6dff;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
}
button:hover {
  background: #aaa;
}
.submit {
  text-align: center;
}
.error {
  color: red;
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
}
h1 {
  font-family: "Grand Hotel", "cursive";
  font-size: 48px;
}
@import url("https://fonts.googleapis.com/css2?family=Grand+Hotel&display=swap");
</style>
