<template>
 <div>
	Задача 6. Створити компонент - форму для вводу даних кредитної карти <br>
	(на зразок поданого прикладу). При вводі “EXPIRY DATE” розділювач “/” <br>
	додається автоматично.
 </div>
<form-card v-model:cardNumber="userCard" v-model:cardDate ="userDate" v-model:cardCode="userCode"/>
</template>
<script>
import FormCard from './components/FormCard.vue'

export default {
  name: "App",
  components: {
		FormCard
  },
	data(){
		return{
			userCard:null,
      userDate:null,
			userCode:null,
		}
	}
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
