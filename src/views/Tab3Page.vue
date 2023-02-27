<template>
<app-layout :title="title">

<ion-card style="border-radius:5px;box-shadow:none;">
<ion-card-header>
<ion-card-title style="text-align:center;font-weight:bold;">My Route Description</ion-card-title>

</ion-card-header>

<ion-card-content>
<p>You are required to assess or report on music users within your specified route as instructed by your field officer.</p>

<div>

<ion-spinner v-if="isLoading==true"></ion-spinner>
<table style="margin-top:20px;" v-else>
<thead>
<tr>
<th>Date</th>
<th>Start From</th>
<th>Stop At</th>
</tr>
</thead>
<tbody>
<tr v-for="n in route" :key="n.id">
<td style="border-right:none;">
{{ n.date }}
</td>
<td style="border-right:none;border-left:none;">
{{ n.from }}
</td>
<td style="border-left:none;">
{{ n.to }}
</td>
</tr>

</tbody>

</table>
</div>


</ion-card-content>
</ion-card>

</app-layout>
</template>

<script>
import axios from 'axios';
import AppLayout from '@/components/AppLayout.vue'
 import { IonCard, IonCardContent, IonCardHeader,  IonCardTitle, IonSpinner } from '@ionic/vue';
export default {
components:{
AppLayout,
IonCard,
IonCardContent,
IonCardHeader,
IonCardTitle,
IonSpinner
},

data(){return{
title:'Routing',
isLoading:false,
route:[],


}},

methods:{
row(){
this.isLoading=true;
axios.get('../../db/routing.json').then(response=>{
this.isLoading=false;
this.route=response.data.route;
}).catch(error=>{
alert(error);
});

}

},

mounted(){
this.row();
}



}
</script>

<style scoped>

table tr th{
padding:10px;
}

table tr td{
padding:10px;
border:solid thin silver;
text-align: center;
}


</style>
