<template>
	 <section>
      <ol>
        <li v-for="(aluno,index) in list">
          {{ aluno.firstname }}
          {{ aluno.lastname }}
          <button @click="removeStudant(index)">X</button>
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
	},
	methods:{
		removeStudant(value){
			this.$emit('removeStudant',value)
			this.$emit('remove', true)
		}

	}
}
	
</script>
<style scoped>
	
</style>