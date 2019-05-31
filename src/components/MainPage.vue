<template>
    <div>
        <div class="formulario">
            <b-input-group prepend="Nome" class="mt-3">
                <b-form-input v-model="nome"/>
                <b-input-group-append class="campo-nome">
                    <b-button v-on:click="gerarContas" variant="info">Gerar Contas</b-button>
                </b-input-group-append>
                <b-spinner class="loader" v-bind:style="{display: display}" variant="primary" label="Spinning"></b-spinner>
            </b-input-group>
        </div>
        <div class="tabela">
            <b-table striped hover :items="items"></b-table>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'MainPage',
    props: {},
    data() {
      return {
        display: "none",
        nome:"",
        items: []
      }
    },
    methods: {
        gerarContas: function() {
            if(this.nome !== null && this.nome !== ""){
                this.display=""
                axios.post('https://avamec-account-generator.herokuapp.com/create_users/'+this.nome)
                    .then(response => {
                        this.display="none"
                        this.items = response.data.map(data => {
                            return {
                                nome_completo: data.nomeCompleto,
                                email: data.email,
                                senha: "ufrgs2019"
                            }
                        })
                    })
                    .catch(error => { 
                        this.display="none"
                        alert(error) 
                    })    
            } else {
                alert("É obrigatório introduzir um nome para semente.")
            }
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.formulario{
    color: #42b983;
    margin-left: 5em;
    margin-right: 90em;
    margin-top: 5em;
}

.campo-nome{
    margin-right: 1em;
}

.tabela{
    margin-top: 5em;
    margin-left: 5em;
    margin-right: 40em;
}

@media only screen and (max-width: 1600px) {
    .formulario{
        margin-top: 2em;
        margin-left: 5em;
        margin-right: 55em;
    }
    .tabela{
        margin-top: 1em;
        margin-right: 30em;
    }
}
</style>
