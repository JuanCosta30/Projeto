<template>
    <div>
        Bingo do Juan

        <div>
            <p>numeros já sorteados:</p>
            <p>{{ numerosSorteados }}</p>
            <p>Jogadores:</p>
            <p>{{ jogadores }}</p>
        </div>
        <button @click="sortear()">sortear</button>
        <div>
            <label ref='nome' for="nome">Nome:</label>
            <input type="text" id="nome" v-model="nome">
            <label for="sobrenome">sobrenome:</label>
            <input type="text" id="sobrenome" v-model="sobrenome">

        <button @click="adicionarJogador()">Novo Jogador</button>
        </div>
        <Cartela :numerosSorteados="numerosSorteados"></Cartela>
    </div>
</template>

<script>
import Cartela from './Cartela.vue';
export default {
    name: 'BingoDoJuan',
    components: {
        Cartela
    },
    data: () => {
        return {
            numerosSorteados: [7],
            jogadores: [],
            nome:'',
            sobrenome: ''
        }
    },
    methods: {
        sortear() {
            const numero = Number((Math.random() * 75).toFixed(0))
            this.numerosSorteados.push(numero)
        },
        adicionarJogador() {
            const jogador = {
                nome: this.nome,
                sobrenome: this.sobrenome
            }
            this.jogadores.push(jogador)
            this.nome=''
            this.sobrenome=''
            this.$refs.nome.focus()
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
