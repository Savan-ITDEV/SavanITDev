<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col s12 m8 offset-m2">
          <div class="login card-panel green white-text center">
            <h3>Register</h3>
            <form>
              User name:
              <br />
              <div class="input-field">
                <i class="material-icons prefix">email</i>
                <input type="text" id="email" name="email" v-model="email" />
                <label class="white-text" for="email">email</label>
              </div>
              <br />User password:
              <br />
              <div class="input-field">
                <i class="material-icons prefix">lock</i>
                <input type="password" id="password" name="password" v-model="password" />
                <label class="white-text" for="password">password</label>
              </div>
              <button v-on:click="register" class="btn btn-large lighten-4-black-text">Login</button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import firebase from "firebase";
export default {
  name: "register",
  data: function() {
    return {
      email: "",
      password: ""
    };
  },
  methods: {
    register: function(e) {
      //    console.log(this.email);
      firebase
        .auth()
        .createUserWithEmailAndPassword(this.email, this.password)
        .then(
          user => {

            alert(`Account created for ${user.user.email}`);

            this.$router.push("/");
          },
          err => {
            alert(err.message);
          }
        );
      e.preventDefault();
    }
  }
};
</script>
