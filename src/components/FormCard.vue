<template>
 <div class="card__container">
	<label  class="card__number">
		<span>CARD NUMBER</span>
		<div class="card__block"><input ref="cardNumberValue" v-model="cardNumberValue"  class="card__input" type="text" placeholder="4242 4242 4242 4242" maxlength="19">
		<div class="card__image"><img src="../assets/img/Visa.png" alt="visa"></div></div>
	</label>
	<div class="card__content">
		<label  class="card__date">
			<span>EXPIRY DATE</span>
			<input ref="cardDateValue"  v-model="cardDateValue"  type="text" placeholder="MM / YY"  maxlength="7">
		</label>
		<label  class="card__code">
			<span>SECURE CODE</span>
			<div class="code-input">
				<input v-model="cardCodeValue"  class="" type="password" maxlength="3">
				<span>?</span>
			</div>
		</label>
	</div>
</div>
</template>

<script>
	export default {
	name:	'FormCard',
	props: {
		cardNumber: {
			type: String,
			default:null
		},
		cardDate:{
			type:String,
      default:null
		},
		cardCode:{
			type:Number,
			required:true
		},
	},
	computed:{
		cardNumberValue:{
			get(){
				return this.cardNumber
			},
			set(val){
				val = val.replace(/(\d{4}(?=\S+))/g, '$1 ')
				return this.$emit('update:cardNumber', val)
			}
		},
		cardDateValue:{
			get(){
				return this.cardDate
			},
			set(val){
			val = val.replace(/\D/g, "");
      if (val.length >= 1 && val.length < 3) {
      val += " / ";
}
else return val
				return this.$emit('update:cardDate', val)
			}
		},
		cardCodeValue:{
			get(){
				return this.cardCode
			},
			set(val){
				return this.$emit('update:cardCode', val)
			}
		},
	},
mounted(){
this.onFocus()
	},
	methods:{
		onFocus(){
this.$refs.cardNumberValue.focus()
		}
	},

	}
</script>

<style lang="scss" scoped>
.card {

&__container {
	margin: 50px;
	border-radius: 10px;
	background-color: rgba(128, 128, 128, 0.146);
	padding: 20px;
	display: flex;
	flex-direction: column;
	width: 300px;
	height: 150px;
}

&__number {
	position: relative;
	margin-bottom: 20px;
	
}

&__block {
	display: flex;
	justify-content: space-between;
	align-items: center;
	outline:2px solid grey;
	border-radius: 5px;
	background-color: rgb(241, 241, 152);
	 &>input{
width: 80%;
border:none;
	 }
}
&__input{
background-color: rgb(241, 241, 152);
padding: 0  10px;
outline: none;
}
&__image{
width: 45px;
height: 30px;
& img{
	display: inline-block;
	width: 100%;
	height: 100%;
}
}
&__content {
	display: flex;
	gap: 20px;
}

&__date {

}

&__code {
position: relative;
}
}
span{
	display: block;
text-align: left;
margin-bottom: 10px;
}
input{
	outline:2px solid grey;
	border:none;
	border-radius: 5px;
  height: 35px;
	width: 90%;
	padding-left: 10px;
}
.code-input {
	display: flex;
	justify-content: space-between;
	align-items: center;
	gap: 10px;
	outline:2px solid grey;
	border-radius: 5px;
  background-color: white;
	padding:0 5px;
	// position: relative;
	// z-index: -1;
	& input{
		width: 40%;
outline:none;
	}
	& > span{
		display: inline-flex;
		justify-content: center;
		align-items: center;
		color:white;
		width: 30px;
		height: 30px;
		background-color: rgb(0, 115, 255);
		border-radius:50%;
		margin: 0;
	}
 
}
</style>