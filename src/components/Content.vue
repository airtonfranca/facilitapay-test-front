<template>
  <div>
    <v-app class="container">
      <div class="form">
        <div>
          <v-form ref="form" v-model="valido" lazy-validation>
            <v-text-field-money
              v-model="valor"
              label="Você envia"
              :properties="{
                prefix: moeda,
                readonly: false,
                disabled: false,
                outlined: false,
                clearable: true,
                placeholder: ' '
              }"
            />
          </v-form>
        </div>
        <div class="v-select-a">
          <v-select
            class="custom"
            v-model="select"
            :items="paises"
            label="Moeda Origem"
            item-text="nome"
            item-valor="nome"
            return-object
            single-line
            text-color="white"
          >
            <template v-slot:item="slotProps">
              {{ slotProps.item.nome }}
            </template>
          </v-select>
        </div>
      </div>
      <div class="painel">
        <ul>
          <span></span>
          <li>{{ selectnome }} 1 = {{ selectnome2 }} {{ taxa }}</li>
          <span></span>
          <li>IOF (1.10%) = {{ selectnome }} {{ iof }}</li>
          <span></span>
          <li>Taxa Administrativa = {{ selectnome }} {{ fx }}</li>
        </ul>
      </div>
      <div class="form2">
        <div>
          <v-form ref="form" v-model="valido">
            <v-text-field-money
              v-model="valorconvertido"
              label="Beneficiário recebe"
              :properties="{
                prefix: moeda2,
                readonly: false,
                disabled: false,
                outlined: false,
                clearable: true,
                placeholder: ' '
              }"
            />
          </v-form>
        </div>
        <div class="v-select-a">
          <v-select
            v-model="select2"
            :items="paises2"
            label="Moeda Destino"
            item-text="nome"
            item-valor="nome"
            return-object
            single-line
          >
            <template v-slot:item="slotProps">
              {{ slotProps.item.nome }}
            </template>
          </v-select>
        </div>
      </div>
    </v-app>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  data: () => {
    return {
      envia: 0,
      valido: true,
      valor: 0,
      select: { nome: "Escolha a moeda", valor: "" },
      select2: { nome: "Escolha a moeda", valor: "" },
      paises: [
        {
          nome: "Escolha a moeda",
          valor: ""
        },
        {
          nome: "EUR",
          valor: "EUR"
        },
        {
          nome: "BRL",
          valor: "BRL"
        },
        {
          nome: "USD",
          valor: "USD"
        }
      ],
      paises2: [
        {
          nome: "Escolha a moeda",
          valor: ""
        },
        {
          nome: "EUR",
          valor: "EUR"
        },
        {
          nome: "BRL",
          valor: "BRL"
        },
        {
          nome: "USD",
          valor: "USD"
        }
      ]
    };
  },
  computed: {
    selectnome(): string {
      let nome = "";
      if (this.select?.nome == "EUR") nome = "EUR";
      if (this.select?.nome == "BRL") nome = "BRL";
      if (this.select?.nome == "USD") nome = "USD";
      return nome;
    },
    selectnome2(): string {
      let nome2 = "";
      if (this.select2?.nome == "EUR") nome2 = "EUR";
      if (this.select2?.nome == "BRL") nome2 = "BRL";
      if (this.select2?.nome == "USD") nome2 = "USD";
      return nome2;
    },
    calciof(): number {
      return this.valor * 0.011;
    },
    calcfx(): number {
      return this.valor * 0.01;
    },
    iof(): string {
      return this.calciof.toLocaleString("pt-br", {
        minimumFractionDigits: 2
      });
    },
    fx(): string {
      return this.calcfx.toLocaleString("pt-br", {
        minimumFractionDigits: 2
      });
    },
    taxa(): number {
      if (this.select?.valor == "EUR" && this.select2?.valor == "BRL") {
        return 6.397;
      }
      if (this.select?.valor == "EUR" && this.select2?.valor == "USD") {
        return 1.2206;
      }
      if (this.select?.valor == "BRL" && this.select2?.valor == "EUR") {
        return 0.1563;
      }
      if (this.select?.valor == "BRL" && this.select2?.valor == "USD") {
        return 0.1917;
      }
      if (this.select?.valor == "USD" && this.select2?.valor == "EUR") {
        return 0.8192;
      }
      if (this.select?.valor == "USD" && this.select2?.valor == "BRL") {
        return 5.2164;
      } else return 1;
    },
    valorconvertido(): number {
      return (this.valor - this.calciof - this.calcfx) * this.taxa;
    }
  }
});
</script>
<style scoped>
.v-application {
  background-color: transparent !important;
}
.form,
.form2 {
  display: flex;
  width: 600px;
  margin: 0 auto 30px;
}
.form {
  margin-top: 93px;
}
.v-form {
  color: #fff;
  margin-right: 20px;
  width: 160%;
  padding: 3px 20px 0px 3px;
  border-radius: 3px;

  background-color: #fff;
}
.v-select-a {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #3c485f;
  z-index: 10;
  height: 74px;
  border-radius: 0 3px 3px 0;
  padding: 10px;
  color: #fff;
  text-decoration: none;
}
.v-select {
  width: 170px;
  color: #fff;
}
.painel {
  margin: 0 auto 20px;
  padding-left: 10px;
  width: 520px;
  font-size: 14px;
  color: white;
}
span {
  width: 20px;
  height: 20px;
  border-radius: 10px;
  background-color: rgb(66, 61, 61);
  display: block;
  float: left;
}
.painel li {
  list-style-type: none;
}
.v-select-a__selection {
  color: #fff !important;
}
</style>
