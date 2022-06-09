<template>
  <form @submit.prevent="handleSubmit()">
    <label>Email:</label>
    <input type="email" required v-model="email" />
    <label>Password:</label>
    <input type="password" required v-model="password" />
    <div v-if="passwordError" class="error">{{ passwordError }}</div>
    <label>Role:</label>
    <select v-model="role">
      <option value="dragon1">dragon1</option>
      <option value="dragon2">dragon2</option>
    </select>
    <div>
      <input type="checkbox" value="a" v-model="names" />
      <label>a</label>
      <input type="checkbox" value="b" v-model="names" />
      <label>b</label>
      <input type="checkbox" value="c" v-model="names" />
      <label>c</label>
    </div>
    <div>
      <label>skills</label>
      <p class="hint">press (alt + ,) to add skill</p>
      <input type="text" v-model="tempSkill" @keyup.alt="addSkill($event)" />
      <div v-for="skill in skills" :key="skill" class="pill">
        <div @click="deleteSkill(skill)">
          {{ skill }}
        </div>
      </div>
    </div>
    <div>
      <input type="checkbox" v-model="terms" />
      <label>Accept terms and conditions</label>
    </div>
    <div class="submit"><button>Submit</button></div>
  </form>
  <!-- <p>email:{{ email }}</p>
  <p>password:{{ password }}</p>
  <p>role:{{ role }}</p>
  <p>terms:{{ terms }}</p>
  <p>names:{{ names }}</p> -->
</template>
<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      terms: false,
      names: [],
      tempSkill: "",
      skills: [],
      passwordError: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill))
          this.skills.push(this.tempSkill);
        this.tempSkill = "";
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item;
      });
    },
    handleSubmit() {
      this.passwordError =
        this.password.length > 5 ? "" : "password should be 6 char long";
      if (!this.passwordError) {
        var p = (p1) => console.log(p1);
        p("email: " + this.email);
        p("password: " + this.password);
        p("role: " + this.role);
        p("namesSeleted: " + this.names);
        p("skills: " + this.skills);
        p("isTermAccepted: " + this.terms);
      }
    },
  },
};
</script>
<style>
form {
  max-width: 420px;
  background: white;
  margin: 30px auto;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  /* font-size: 0.6em; */
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  color: #555;
  display: block;
  padding: 10px 6px;
  width: 100%;
  border: none;
  border-bottom: 1px solid #ddd;
  box-sizing: border-box;
}
input[type="checkbox"] {
  display: inline-block;
  position: relative;
  width: 16px;
  margin: 0px 10px 0px 0px;
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
  background: #06bdff;
  border: 0;
  padding: 10px 20px;
  border-radius: 20px;
  color: white;
  margin-top: 20px;
}
.submit {
  text-align: center;
}
.error,
.hint {
  color: #ff0062;
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
}
.hint {
  color: #777;
}
</style>