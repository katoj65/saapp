<template>
  <ion-page>
    <ion-tabs>
      <ion-router-outlet></ion-router-outlet>
      <ion-tab-bar slot="bottom">
        <ion-tab-button tab="tab1" href="/tabs/tab1">
          <ion-icon aria-hidden="true" :icon="podium" />
          <ion-label>Assessment</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab2" href="/tabs/tab2">
          <ion-icon aria-hidden="true" :icon="shieldCheckmark" />
          <ion-label>Reporting</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab3" href="/tabs/tab3">
          <ion-icon aria-hidden="true" :icon="map" />
          <ion-label>Routing</ion-label>
        </ion-tab-button>
      </ion-tab-bar>
    </ion-tabs>
  </ion-page>
</template>

<script>
import { IonTabBar, IonTabButton, IonTabs, IonLabel, IonIcon, IonPage, IonRouterOutlet } from '@ionic/vue';
import { ellipse, square, triangle, podium, shieldCheckmark, map } from 'ionicons/icons';

export default{
components:{
IonTabBar,
IonTabButton,
IonTabs,
IonLabel,
IonIcon,
IonPage,
IonRouterOutlet

},

setup(){return{

ellipse, square, triangle, podium, shieldCheckmark, map


}}




}








</script>
