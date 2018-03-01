<template>
<div class="principal">
  <header class="principal-01">
    <h1>Lista de Alunos</h1>
  </header>
  <main>
    <section>
      <form class="secund">
        <!-- <section class="secund-o1" -->
          <label>Ordenado por:</label>
          <select class="rap" v-model="configs.orderBy">
            <option value="lastname">Ultimo Nome</option>
            <option value="firstname">Primeiro Nome</option>
          </select><br><br>
          <label>Ordem:</label>
          <select class="rap-1" v-model="configs.order">
            <option value="asc">Crescente</option>
            <option value="desc">Decrescente</option>
          </select><br><br>

          <label>Filtrar</label>
          <input type="text" class="form-control" placeholder="Filtrar por nome" v-model="configs.filter">
      </form>
    </section>
    <ListaAlunos 
      :list="list"
      @removeStudant="value => {removeStudant = value}"
      @remove="value => {remove = value}"
    ></ListaAlunos>

  </main>
</div>  
</template>
<script>
import _ from 'lodash'
import ListaAlunos from './ListaAlunos'

export default{
  name:'Geraldo',
  data(){
     return {
      remove:false,
      removeStudant:'',
      configs:{
        orderBy: 'firstname',
        order: 'desc',
        filter: '',
      },
      alunos:[
        {
          firstname:'Geraldo',
          lastname:'Volcy'
        },
        {
          firstname:'Romulo',
          lastname:'Tunala'
        },
        {
          firstname:'Gabriel',
          lastname:'Milao'
        },
        {
          firstname:'Guilherme',
          lastname:'Oliviera'
        },
        {
          firstname:'Rafael',
          lastname:'Luis'
        },
      ]
    }
  },
  watch:{
    removeStudant(){
      if(this.remove === true) {
        this.alunos.splice(this.removeStudant,1)
        this.remove = false
        this.removeStudant = ''
      }
    }
  },
  computed: {
    list() {
      const filter = this.configs.filter;
      const list = _.orderBy(this.alunos, this.configs.orderBy, this.configs.order);

      if (_.isEmpty(filter)) {
        return list;
      }
     
       return _.filter(list, aluno => aluno.firstname.indexOf(filter) >= 0);
    
    }

  },
  components:{
    ListaAlunos
  }
}

</script>

<style>
 .principal{ 
       background-color: #8B4513;
       color: #000;
       display: flex;
       align-items: center;
       justify-content: space-around;
        }
  .principal-01{
       color: #000;
       display: flex;
       align-items:;
       justify-content:;
       background-color: red;
       padding-top: 100px;
       padding-bottom: 100px;
       padding-right:30px; 
       padding-left:30px;
        }
 .secund{
       color: #fff;
       margin-top: 10%;

     }
 .rap{
 }




</style>