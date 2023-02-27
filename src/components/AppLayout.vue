<template>
<ion-page id="bg">
<ion-header style="background:#C53683;">
<ion-toolbar>
<ion-buttons slot="start">
<ion-button>
<ion-icon :icon="menuOutline"></ion-icon>
</ion-button>
</ion-buttons>
<ion-title style="font-weight:bolder;">{{ title }} </ion-title>
<ion-buttons slot="end">
<ion-button @click="navigate('/assessed')">
<ion-icon :icon="save"></ion-icon>
</ion-button>
<ion-button>
<ion-icon :icon="searchOutline"></ion-icon>
</ion-button>
<ion-button>
<ion-icon :icon="personCircle"></ion-icon>
</ion-button>
</ion-buttons>
</ion-toolbar>




</ion-header>
<ion-content :fullscreen="true">
<ion-header collapse="condense">
<ion-toolbar>
<ion-title size="large">Tab 1</ion-title>
</ion-toolbar>
</ion-header>
<slot></slot>
</ion-content>
</ion-page>
</template>

<script>
import { menuOutline, searchOutline, personCircle, save} from 'ionicons/icons';
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent,IonButtons, IonButton, IonIcon } from '@ionic/vue';
export default {
components:{
IonPage,
IonHeader,
IonToolbar,
IonTitle,
IonContent,
IonButtons,
IonButton,
IonIcon
},

props:{
title:{},
},

data(){return{
item:[],



}},

setup(){
return{
menuOutline,
searchOutline,
personCircle,
save
}
},

methods:{
navigate(item){
this.$router.push(item);
}



}





}
</script>
<style scoped>
#bg{
background:#C53683;
}

ion-content{
--background-color:'red'
}

 ion-toolbar {
    --background:#C53683;
    --color: white;

  }

  ion-content::part(background) {
    background: #F8BBD0;
  }

</style>