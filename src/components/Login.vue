<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col s12 m8 offset-m2">
          <div class="login card-panel blue white-text center">
            <h3>Login</h3>
            <form>
              User name:
              <br />
              <div class="input-field">
                <i class="material-icons prefix">email</i>
                <input type="text" name="email" id="email" v-model="email" />
                <label class="white-text" for="email">email</label>
              </div>
              <br />User password:
              <br />
              <div class="input-field">
                <i class="material-icons prefix">lock</i>
                <input type="password" name="password" id="password" v-model="password" />
                <label class="white-text" for="email">password</label>
              </div>
              <button v-on:click="login" class="btn btn-large lighten-4-black-text">Login</button>
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
  name: "login",
  data: function() {
    return {
      email: "",
      password: ""
    };
  },
  methods: {
    login: function(e) {
      //    console.log(this.email);
      firebase
        .auth()
        .signInWithEmailAndPassword(this.email, this.password)
        .then(
          user => {
            alert(`You are logged is as ${user.user.email}`);

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
