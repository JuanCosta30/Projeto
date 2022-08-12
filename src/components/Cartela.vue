<template>
  <div>
    <p>Jogador: {{nomeJogador}}</p>
    <table style='margin:auto'>
        <tr v-for="(linha,index) of numeros" :key="index">
        <td v-for="(numero,index) of linha" :key="index">
            <div v-if="numeroFoiSorteado(numero)" style="color:red">{{numero}}</div>
            <div v-else style="color:black">{{numero}}</div>
        </td>
        </tr>
    </table>
  </div>
</template>

<script>

export default {
  name: 'BingoDoJuan',
  props: {
    numerosSorteados:[],
  },
  data: () => {
    return {
        jogador: {
            nome: "Juan",
            sobrenome: "da Costa"
        },
        numeros: [[12,65,23,7,49]
        ,[12,65,23,7,49]
        ,[12,65,undefined,7,49]
        ,[12,65,23,7,49]
        ,[12,65,23,7,49]
        ]
    }
  },
  computed: {
    nomeJogador() {
        return `${this.jogador.nome} ${this.jogador.sobrenome}`
    }
  },
  methods: {
    numeroFoiSorteado(numero) {
        const foiSorteado = this.numerosSorteados.includes(numero)
        return foiSorteado
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
