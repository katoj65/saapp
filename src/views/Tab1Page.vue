<template>
<app-layout :title="title">




  <ion-card style="border-radius:5px;padding:20px;box-shadow:none;">
    <ion-card-header>
      <ion-card-title style="text-align:center;">Business Details</ion-card-title>
    </ion-card-header>

    <ion-card-content>
    <form>

<div style="margin-bottom:20px;">
<ion-input placeholder="Enter business name" style="height:50px;background:white;border:solid thin gray;border-radius:10px; color:black;"></ion-input>
</div>

<div style="margin-bottom:20px;">
  <ion-select placeholder="Select Business Category" style="height:50px;background:white;border:solid thin gray;border-radius:10px;color:black;">
        <ion-select-option :value="s.name" v-for="s in response.entity" :key="s.id">{{ s.name }} </ion-select-option>
      </ion-select>
</div>

<div style="margin-bottom:20px;">
<ion-input placeholder="Number of employees" style="height:50px;background:white;border:solid thin gray;border-radius:10px;color:black;"></ion-input>
</div>

<div style="margin-bottom:20px;">
<ion-input placeholder="Size of the area" style="height:50px;background:white;border:solid thin gray;border-radius:10px;color:black;"></ion-input>
</div>

<div style="margin-bottom:20px;">
<ion-input placeholder="Number of seats" style="height:50px;background:white;border:solid thin gray;border-radius:10px;color:black;"></ion-input>
</div>

<div style="margin-bottom:20px;">
<ion-input placeholder="Working days" style="height:50px;background:white;border:solid thin gray;border-radius:10px;color:black;"></ion-input>
</div>


<div style="margin-bottom:20px;">
<ion-button expand="block" style="height:50px;border-radius:10px;background:black;border:solid 5px black;">Save</ion-button>
</div>

    </form>
    </ion-card-content>
  </ion-card>








</app-layout>
</template>
<script>
import axios from 'axios';
import AppLayout from '@/components/AppLayout.vue';
 import { IonCard, IonCardContent, IonCardHeader,  IonCardTitle, IonInput, IonButton, IonSelect, IonSelectOption} from '@ionic/vue';
export default {
components:{
AppLayout,
IonCard,
IonCardContent,
IonCardHeader,
IonCardTitle,
IonInput,
IonButton,
IonSelect,
IonSelectOption
},

data(){return{
title:'Assessment',
response:[]

}},

methods:{
row(){
axios.get('../../db/assess.json').then(response=>{
this.response=response.data;
}).catch(error=>{
alert(error);
});



},




},

mounted(){
this.row();
}



}
</script>

<style  scoped>
ion-button {
--background: black;
--background-hover: gray;

}
</style>