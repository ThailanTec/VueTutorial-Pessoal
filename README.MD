## O que é o Vue. JS?

Framework JavaScrip reativo. Que trabalha com praticidade e velocidade.
Seu foco é criar SPA(Single Page Aplication), uma aplicação que não precisa carregar o projeto todo para carregar as informações.

## O que é DOM? (Relembrando)
Forma onde o navegador inteliga o html ao javascript. Doom, todo elemento HTML é um elemento.

# Montando ambiente:

## erramentas necessarias e opcionais. 

1 - Node JS
2 - Vue CLI (Para facilitar a criação)

## Para iniciar um projeto, podemos utilizar:

# sudo vue create nomedoprojeto.

Para rodar podemos utilizar o comando dentro da pasta:

npm run serve

## Estrutura pasta/arquivos:

# Babel - Biblioteca para converter os arquivos para os navegadores. 

# Public - Fica o index(Você so precisa de um unico arquivo html), arquivo para renderizar o JS e o favicon icon que podemos alterar se desejar. 

# src:
assets - videos, imagens.

# components - onde deve-se ficar os arquivos de componentes.

# App.vue - Fica responsavel por exibir a pagina. Componente raiz da aplicação.

# main.js - So mecher para instalar biblioteca. Cria uma instancia do views e diz que a raiz é o app e dizemos para montar no #app no index(public).

## O que são componentes? 

R - Cada compenente que você vai adicionando a sua pagina vai ter o seu arquivo. Você separa o codigo da sua aplicação. Um componente é um arquivo.
Sendo dividido em 3 partes HTML/Template, Estilo/CSS e a logica/JavaScript. 
Assim conseguimos organizar melhor o projeto.
Todo arquivo com .vue no final é um componente vue. 
Podemos sempre reutilizar os componentes, chamando o nome deles como se fosse uma tag html. ex: <hellowordvue>

## Criar e utilizar componentes. 

Para criar vamos criar primeira a sua entrutura:

<template>

</template>

<script>

</script>

<style>

</style>

Em seguida escrevemos o codigo que desejamos dentro. Na parte do App.vue, podemos importar o componente criado. Dentro de script.
# import Cliente from "./components/Cliente";

Em seguida no App, export default {
    name: 'App',
    components:{
        Clientes
    }
}

Para que o App, entenda a nossa chamada e faça a exibição.

# O componente so pode ter apenas uma tag html dentro, ideal que seja tudo adicionado dentro de uma div. 


## Reatividade 
Toda vida que o seu dado muda, toda local que ta com seu dado vai ser alterado. Reagindo e alterando o HTML.

# Interpolação:
{{}}, utilizamos duas chaves para podermos utilizar codigo javascrip dentro dele. 

ex: {{2+2+5}}, no front vai no retornar esse dado.

Dessa forma podemos passar dados javascript padrão e chamar dentro desse campo. Ex:

<script>
export default {

    data(){
    return{
        nome: "Thailan",
        numero: 221212121 ,
        idade: 21,
        email: "thailan@thailan.com.br"

    }
    }
    
}
</script>

E depois podemos passar esses dados dentro do template e utilizar no front da nossa aplicação. 

## Data Binding
Existe dois tipos de data binding. Um com um caminho e outro com 2 caminhos.

# One way data binding:
Servindo apenas para exibição de dados.
Para utilizarmos uma variavel dentro de uma tag html, passamos na frente do dado um :(dois pontos). Ex:

<input type="text" :value="numero">

Dessa forma conseguimos passar os dados de uma variavel dentro. Apenas exibindo dados.

# Two way data binding(com V-model):
Servindo para mudar dados da variavel dentro da aplicação. Não funciona em todo tipo de atributo. 

# Para aplicar:
Passa ao envez do campo padrão do html, passamos v-model e o nome da variavel em seguida.Ex:

<input type="text" v-model="email">

Onde em qualquer lugar onde tiver essa variavel, no caso do exemplo tem um campo e então podemos alterar de todo o site. 

--------------------------------------------------------------------------------------------

## Props

Elas vão permitir que você passe os dados do componentes durante a criação dele.

Para criar, podemos ir no script em questão. Criar um objeto chamado props e passar os atributos que queremos receber e passamos o tipo dele. Ex:

 props: {
        nome: String,

    }
E para definir o nome dentro das props, podemos passar dentro da chamada no app o dado que foi passado dentro do propos. Ex:

<Clientes nome="Thailan"/>

Passando assim a informação apenas para aquele "cliente" em questão. 

Assim cada componente vai ter seu tipo de dado.

Passando dados do componente pai para o componente filho.

# Diretivas condicionais com v-if

Diretivas são tags que não temos no html normal. Ex: v-model

Podemos definir para exibir campos utilizando o v-if, assim o campo so deve aparecer caso a expressão seja verdadeira ou falsa, ou caso ditarmos uma regra de negocio na aplicação. Ex:

Aqui estamos dizendo que so vamos mostrar a idade caso ela seja verdadeira. Isso no App.vue
 <Cliente :cliente="clientevictor" :showIdade="true" />

 E no Cliente.vue, passamo as seguinte informações:

  <h4 v-if="showIdade === true">Idade: {{cliente.idade}}</h4>

  Utilizando de um v-if, uma diretiva do vue, informamos a regra de negocio onde vai ser seguida. Nesse caso a idade so vai mostrar no front caso ela seja verdadeira o booleano.

# Diretivas condicionais com v-else

  Devem ser utilizadas seguidas do v-if. Não nessecita passar parametros, automaticamente ele reconhece a logica e aplica seguindo, caso a expressão seja verdadeira ou falsa. Ficando da seguinte forma:

   <h4 v-else> O usuario escondeu a idade.</h4>

# Diretivas condicionais com v-show

Ela funciona como um if. Diferente ele acaba que mostra no front, 

E nele não podemos utilizar um else.

# Diretivas condicionais com v-else-if

Ele pode receber mais de uma condição seguida das outras.


# Diretivas condicionais com for
Podemos utilizar para que assim não fiquemos repetindo codigo. Ele trabalha semelhando ao foreach, e para usar temos que ter um array.
Para utilizarmos precisamos passar uma key, que vai diferenciar um dado do outro.

Podemos chamar e utilizar da seguinte forma:

<div v-for="cliente in clientes" :key="cliente.id">
            <Cliente :cliente="cliente"/>
</div>

Podemos ainda utilizar de mais uma agregação chamada de index, para exibir a mais no codigo e mostrar sua posição no código.

<div v-for="(cliente,index) in clientes" :key="cliente.id">
           <h1>{{index}}</h1>
            <Cliente :cliente="cliente"/>
</div>

## Classes Condicionais

# Obs: So funciona com classes!

Podemos dizer para quando queremos exibir uma classe para cada tipo de user/cliente. 
Como no caso de um cliente com conta premium. Passamos a seguinte informação dentro da div princiapal:

<div :class="{'cliente': !Isprimium, 'cliente-premium': Isprimium}">

Dessa forma estamos dizendo que se a classe for diferente de Isprimium a que vai prevalecar é a classe Cliente, caso seja verdadeira vai apresentar a classe Isprimium.

## Eventos

Conseguimos capturar eventos de clique do mouse, focar com o mouse e dentre outros. Isso são os eventos que podem ocorrer dentro de uma aplicação.

Para declararmos um evento podemos onde queremos chamar utilizando de um @, e definir qual evento queremos capturar. Ex:

<button @click="mudarCor">Mudar cor!</button>

E em seguidas precisamos criar um methods na área de return. Ex:

methods:{
        mudarCor: function(){
            this.Isprimium = !this.IsprimiumIsprimium
        }
    }

Assim dentro do methods, passamos a função que desejamos que seja cumprida quando clicarmos no botão ele vai mudar de cor, como no exemplo acima.

## Formulario

Serve para cadastro de usuario. Assim podemos fazer de uma forma na qual o cliente digite seus dados e ele vai para o front. Para isso podemos fazer da seguinte forma:

Primeiro criamos as variaveis para receber os dados. Assim:

nomeFiled: "",
emailField: "",
idadeFiled: 0,

Em seguidas precisamos criar um methods para que assim ele possa receber os dados e armazenar. 

methods:{
    cadastrarUsuario: function(){
      this.clientes.push({
        nome: this.nomeFiled,
        email: this.emailField,
        idade: this.idadeFiled,
        id: Date.now()
      })
      this.nomeFiled = "",
      this.emailField = "",
      this.idadeFiled = 0
 Usamos o this para referenciar o que está de fora. E em seguidas removemos os campos.

 ## Validação de formulario
Para isso podemos utilizar logica pura. Como podemos ver abaixo:

 if (this.nomeFiled == "" || this.nomeFiled == " " || this.nomeFiled.length < 3) {
        this.ErroNome == true;
      } else {
        this.clientes.push({
        nome: this.nomeFiled,
        email: this.emailField,
        idade: this.idadeFiled,
        id: Date.now()
      }

## Emissão de Eventos

Serve para que consigamos manipular outros eventos atraves da passagem de parametros.

Obs: Nunca mecher atraves dele nas props.


 ## Filtros 

 Eles servem para processar variaveis que estão bindado no html. Podendo processar a informação sem mudar.

 O filtro sempre recebe um valor e retorna algo. 

 Criamos um campo de filtro:

 filters:{

    processarNome: function(value){
        return value.toUpperCase()
    }

Em seguida passamos o nome do filtro que criamos dentro de onde desejamos que ela seja alterada. 

<h4>Nome: {{cliente.nome | processarEmail }}</h4>

Assim, ele vai trabalhar em cima da solicitação que passamos detro do filtro. Alterando a visualização e não o dado. 


## Computed Properties 

Formas de criar variaveis dinamicas. Assim podemos criar novas strings com dados de diferentes formas:

computed: {
      idEspecial: function(){
          return (this.cliente.email + this.cliente.nome + this.cliente.idade).toUpperCase()
      }
  }

Criamos um computed e em seguidas criamos uma função onde passamos os metodos e unimos os dados .


## Computed e como instalar bibliotecas no Vue

Podemos adicionar funções baixadas por bibliotecas para fazer as coisas como a loadash, auxiliando assim com o trabalho. Para isso so precisamos usar os comando npm e o nome da bibliotecas. 

E em seguidas utilizamos da seguinte forma:

computed: {
    orderClientes: function(){
      return _.orderBy(this.clientes,["nome"], ['asc'])
    }
  }
}


## Como usar framework css no vue

No curso vamos utilzar o bulma. Mas podemos também utilizar qualquer outro que não utilize de Jquery para rodar os codigos em JavaScript. 

Para usar, primeiro vamos no main.js e la importamos o bulma ou qualquer outro projeto. 

import "../node_modules/bulma/css/bulma.css"

