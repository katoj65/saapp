<template>
<ion-app id="bg">
<ion-router-outlet v-if="$store.state.user!=null" />
<login-component v-else></login-component>
</ion-app>
</template>
<script>
import { IonApp, IonRouterOutlet } from '@ionic/vue';
import LoginComponent from '@/components/LoginComponent.vue';
export default{
components:{
IonApp,
IonRouterOutlet,
LoginComponent,

},

data(){return{
title:'',
user:null,



}},

methods:{
access(){
if(this.user!=null){
this.$store.state.user=this.user;
}else{
this.$store.state.user=null;
}
}


},

mounted(){
this.access();
}



}
</script>

<style scoped>
#bg{
background:#C53683;
}


</style>