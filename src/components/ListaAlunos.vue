<template>
	 <section>
      <ol>
        <li v-for="aluno in list">
          {{ aluno.firstname }}
          {{ aluno.lastname }}
        </li>
      </ol>
    </section>
</template>
<script>
export default{
	name:'ListaAlunos',
	props:{
		list:{
			type:Array,
			required:true
		}
	},
	data(){
		return{}
	}
}
	
</script>
<style scoped>
	
</style>