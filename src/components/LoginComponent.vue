<template>
<div>
<img :src="'../../assets/icon/logo1.png'" style="margin-top:-50px;">


<div class="body" style="margin-top:-50px;">
{{ info }}
<div>
<h1>{{ title }} </h1>
</div>
<form @submit.prevent="submit">
<div style="padding:20px;">
<ion-input placeholder="Enter your telephone number" type="number" style="border:solid thin white;background:white;color:black;border-radius:10px;padding:15px;text-align:center;height:50px;" v-model="form.tel"></ion-input>
</div>


<div style="padding:20px;padding-top:0;">
<ion-input placeholder="Enter your password" style="border:solid thin white;background:white;color:black;border-radius:10px;padding:15px;text-align:center;height:50px;" v-model="form.pass"></ion-input>
</div>


<div style="padding:20px;padding-top:0;">
<ion-button type="submit" expand="block" style="background:black;border-radius:10px;border:solid 5px black;box-shadow:none;height:50px;" color="black">Login</ion-button>
</div>

<div v-if="error!=null" style="color:white;text-align:center;padding:10px;">
{{ error }}
</div>

</form>

</div>


</div>
</template>
<script>
import axios from 'axios';
import { IonInput, IonButton } from '@ionic/vue';
import { Preferences } from '@capacitor/preferences';
export default {
components:{
IonInput,
IonButton

},

data(){return{
title:'LogIn',
info:null,
error:null,
//
form:{
tel:'0752567534',
pass:'123456789',
},



}},


methods:{

submit(){
this.error=null;
if(this.form.tel!=null && this.form.pass!=null){
axios.get('../../db/login.json')
.then(response =>{
const item=response.data.user;
item.forEach(element => {
if(element.tel==this.form.tel && element.pass==this.form.pass){
this.$store.state.user=element;
Preferences.set({ key:'tel',value:element.tel});
Preferences.set({ key:'fname',value:element.firstname});
}else{
this.error='Invalid telephone number or password.';
}
});
}).catch(error=>(alert(error)));
}else{
this.error='Fill in the telephone number and password.';
}
}





}





}
</script>

<style scoped>
.body{
padding:10px;
}

.body div h1{
color:white;
text-align: center;
}

ion-input .custom{
--background: white;
--color: black;
--placeholder-color:black;
--placeholder-opacity: .8;

--padding-bottom: 10px;
--padding-end: 10px;
--padding-start: 10px;
--padding-top: 10px;
}


ion-button {
--background: black;
--background-hover: silver;


}

</style>