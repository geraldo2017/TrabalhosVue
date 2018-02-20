<template>
<div class="principal">
  <header class="principal-01">
    <h1>Lista de Alunos</h1>
  </header>
  <main>
    <section>
      <form class="secund">
        <!-- <section class="secund-01"> -->
          <label>Ordenado por:</label>
          <select class="rap-1" v-model="configs.orderBy">
            <option value="lastname">Ultimo Nome</option>
            <option value="firstname">Primeiro Nome</option>
          </select><br><br>
        <!-- </section>
        <section class="secund-02"> -->
          <label>Ordem:</label>
          <select class="rap-2" v-model="configs.order">
            <option value="asc">Crescente</option>
            <option value="desc">Decrescente</option>
          </select>
        <!-- </section> -->
      </form>
    </section>
    <section>
      <ol>
        <li v-for="aluno in list">
          {{ aluno.firstname }}
          {{ aluno.lastname }}
        </li>
      </ol>
    </section>
  </main>
</div>  
</template>
<script>
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
      return _.orderBy(this.alunos, this.configs.orderBy, this.configs.order); 
      
      //  if (_.isEmpty(filter)) {
      //   return list;
      // }
      
    },

  }
}
</script>

<style>
  
</style>