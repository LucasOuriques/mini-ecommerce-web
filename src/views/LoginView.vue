<template>
    <div style="font-size: 2rem; font-weight: bold;">
      <p class="title">Tech Sales</p>
  
      <v-form style="width: 50%; margin: auto;"
        ref="formdodani"
        v-model="formValido">

        <v-text-field v-model="dados.nome" label="Usuário" :rules="[rules.required]"></v-text-field>
        <v-text-field type="password" v-model="dados.senha" label="Senha" :rules="[rules.counter]"></v-text-field>
        <p class="space">
            <a class="redefinir" href="/reset-password"><h3>Esqueceu a sua senha?</h3></a>

            <v-btn @click="validate(); redirecionar()" :disabled="!formValido" class="button-entrar">
                Entrar
            </v-btn>
        </p>

        <p class="space" style="margin-top: 20px">
            <a class="texto"><h3>Ainda não tem uma conta?</h3></a>

            <v-btn @click="redirecionarCadastro()" class="button-entrar">
                Cadastre-se
            </v-btn>
        </p>
    
      </v-form>
    </div>
  </template>
  
  <script>
  export default ({
    name: 'LoginView',
    data() {
      return {
        rules:{
          required: (value) => !!value || 'Campo obrigatório.',
          counter: (value) => value && value.length >= 6 || 'Senha inválida',
        },
        dados: {
          nome: null,
          senha: null,
        },
        formValido: false,
      };
    },
    methods: {
      validate() {
        this.$refs.formdodani.validate();
      },
      reset() {
        this.$refs.formdodani.reset();
      },
      redirecionar() {
        this.$router.push('/home');
      },
      redirecionarCadastro() {
        this.$router.push('/register-user'); 
      },
    },
  })
  </script>

  <style lang="scss">
    .redefinir {
        font-size: 13px;
        text-decoration: none !important;
        color: #085caf;

        :hover {
            text-decoration: underline;
            color: black;
        }
    }

    .texto {
        font-size: 13px;
        text-decoration: none !important;
    }

    .title {
        margin: 15px;
    }

    .space {
        display: flex;
        justify-content: space-between;
        margin: none;
        .button-entrar {
            margin-left: 50%;
            color: white;
            background-color: black;
        }
    }
  </style>
  