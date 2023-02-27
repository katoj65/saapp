<template>
<app-layout :title="title">
<div style="margin:10px;border-radius:10px;padding-top:10px;background:white;padding-bottom:10px;">
<ion-item button detail="true" :detailIcon="caretForwardOutline" v-for="b in business" :key="b.id" lines="full">
<ion-label>
<h3 style="font-weight:bold;font-size:16px;">{{ b.name }} </h3>
<p style="color:silver;">{{ b.count }} businesses assessed</p>
</ion-label>
</ion-item>
</div>
</app-layout>
</template>
<script>
 import { IonItem, IonLabel } from '@ionic/vue';
  import { caretForwardOutline } from 'ionicons/icons';
import axios from 'axios';
import AppLayout from '@/components/AppLayout.vue';
export default {
components:{
AppLayout,
IonItem,
IonLabel

},
data(){return{
title:'Businesses',
business:[],



}},
setup(){
return{
caretForwardOutline,
}
},

methods:{
row(){
axios.get('../../db/assess.json').then(response=>{
this.business=response.data.entity;
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