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
          <select class="rap" v-model="configs.order">
            <option value="asc">Crescente</option>
            <option value="desc">Decrescente</option>
          </select><br><br>

          <label>Filtrar</label>
          <input type="text" class="form-control" placeholder="Filtrar por nome" v-model="configs.filter">
      </form>
    </section>
    <ListaAlunos :list="list"></ListaAlunos>
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
       color: #fff;
       display: flex;
       align-items:center;
        }
  .principal-01{ 
       
        }
 .secund{
       color: #fff;
       height:;
       display:;
       align-items:;
       justify-content:;

        }




</style>