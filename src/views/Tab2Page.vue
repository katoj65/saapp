<template>
 <app-layout :title="title">

<ion-list :inset="true" style="border-radius:5px;margin:10px;">
<ion-item v-for="n in report" :key="n.id">
<ion-label style="font-weight:bolder;">{{ n.name }} </ion-label>
</ion-item>
</ion-list>


<ion-list :inset="true" style="border-radius:5px;margin:10px;">
<ion-item v-for="d in document" :key="d.id">
<ion-label style="font-weight:bolder;">{{ d.name }} </ion-label>
</ion-item>
</ion-list>


<ion-list :inset="true" style="border-radius:5px;margin:10px;">
<ion-item v-for="u in ura" :key="u.id">
<ion-label style="font-weight:bolder;">{{ u.name }} </ion-label>
</ion-item>
</ion-list>

</app-layout>
</template>

<script>
import axios from 'axios';
import AppLayout from '@/components/AppLayout.vue'
 import { IonItem, IonLabel, IonList } from '@ionic/vue';
export default {
components:{
AppLayout,
IonItem,
IonLabel,
IonList
},


data(){
  return{
title:'Reporting',
report:[],
document:[],
ura:[],


  }
},

methods:{
row(){
axios.get('../../db/report.json').then(response=>{
this.report=response.data.reports;
this.document=response.data.documents;
this.ura=response.data.ura;
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