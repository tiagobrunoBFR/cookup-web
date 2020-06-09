<template>
  <form @keydown="error=false" @submit.prevent="submit" action="#" class="sign-in-htm">
    <br />
    <div class="group">
      <v-spacer></v-spacer>
      <base-input
        attributeError="E-mail"
        label="E-mail"
        v-model="email"
        :v="$v.email"
        singleLine
        outlined
        classInput="white--text"
        color="#6a6f8c"
        dark
      >
        <span slot="style">
          <span style="color: white">E-mail</span>
        </span>
      </base-input>
    </div>
    <div class="group">
      <base-input
        attributeError="Senha"
        label="Senha"
        v-model="password"
        :v="$v.password"
        singleLine
        outlined
        classInput="white--text"
        color="#6a6f8c"
        dark
      >
        <span slot="style">
          <span style="color: white">Senha</span>
        </span>
      </base-input>
    </div>

    <div class="group">
      <v-layout align-center justify-center row fill-height>
        <span class="red--text" v-if="error">Credenciais Inválidas</span>
      </v-layout>
    </div>

    <div class="group">
      <input class="check" id="check" type="checkbox" v-model="keepSignedIn" />
      <label for="check">
        <span class="icon"></span> Manter Conectado
      </label>
    </div>

    <div class="group">
      <input class="button" type="submit" value="Login" />
    </div>

    <!-- <div class="foot-lnk">
      <a href="#forgot">Esqueceu sua senha?</a>
    </div>-->
  </form>
</template>

<script>
import { required, email } from "vuelidate/lib/validators";

export default {
  validations() {
    return {
      email: {
        required,
        email
      },
      password: {
        required
      }
    };
  },
  data() {
    return {
      email: "",
      password: "",
      error: false,
      keepSignedIn: true
    };
  },
  methods: {
    async submit() {
      this.$v.$touch();
      if (!this.$v.$invalid) {
        console.log("passou pela validação");
      } else {
        console.log("errou");
      }
    }
  }
};
</script>
