<template>
  <div id="background-page">
    <v-app id="inspire">
      <div id="main">
        <v-container fill-height fluid>
          <v-layout align-center justify-center>
            <v-flex lg3 md4 sm6 x12 x13>
              <div class="login-wrap">
                <div class="login-html">
                  <input
                    @change="navigate"
                    checked
                    class="sign-in"
                    id="tab-1"
                    name="tab"
                    type="radio"
                    value="signin"
                  />
                  <label class="tab" for="tab-1">Login</label>

                  <input
                    @change="navigate"
                    class="sign-up"
                    id="tab-2"
                    name="tab"
                    type="radio"
                    value="signup"
                  />
                  <label class="tab" for="tab-2">Cadastre-se</label>

                  <div class="login-form">
                    <sign-in @do-sign-in="doSignIn" v-if="islogin" />
                    <sign-up v-if="!islogin" />
                  </div>
                </div>
              </div>
            </v-flex>
          </v-layout>
        </v-container>
      </div>
    </v-app>
  </div>
</template>

<script>
import SignIn from "@/components/auth/SignIn";
import SignUp from "@/components/auth/SignUp";

export default {
  components: {
    SignIn,
    SignUp
  },
  data() {
    return {
      navigation: "signin",
      islogin: true
    };
  },
  methods: {
    navigate() {
      var self = this;

      return setTimeout(function() {
        self.islogin = !self.islogin;
      }, 350);
    }
  }
};
</script>

<style src="../../assets/css/authStyle.css"></style>