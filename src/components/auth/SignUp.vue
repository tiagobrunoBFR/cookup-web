<template>
  <form @submit.prevent="onSubmit" action="#" class="sign-up-htm">
    <br />
    <div class="group">
      <base-input
        attributeError="Nome"
        label="Nome"
        v-model="name"
        :v="$v.name"
        singleLine
        outlined
        classInput="white--text"
        color="#6a6f8c"
        dark
      >
        <span slot="style">
          <span style="color: white">Nome</span>
        </span>
      </base-input>
    </div>
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
      <base-input
        attributeError="Confirmar Senha"
        label="Confirmar Senha"
        v-model="passwordConfirmation"
        :v="$v.passwordConfirmation"
        singleLine
        outlined
        classInput="white--text"
        color="#6a6f8c"
        dark
      >
        <span slot="style">
          <span style="color: white">Confirmar Senha</span>
        </span>
      </base-input>
    </div>

    <div class="group">
      <input class="button" type="submit" value="Salvar" />
    </div>
  </form>
</template>

<script>
import { minLength, required, sameAs, email } from "vuelidate/lib/validators";

export default {
  name: "SignUp",

  validations() {
    return {
      name: {
        required
      },
      email: {
        email,
        required
      },
      password: {
        required,
        minLength: minLength(6)
      },

      passwordConfirmation: {
        required,
        sameAs: sameAs("password")
      }
    };
  },

  data() {
    return {
      email: "",
      password: "",
      name: "",
      passwordConfirmation: ""
    };
  },

  methods: {
    onSubmit() {
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

