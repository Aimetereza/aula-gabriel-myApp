<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Galeria de fotos</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">

      <ion-grid>
        <ion-row>
          <ion-col size="4" :key="photo" v-for="photo in photos">
            <ion-img :src="photo.webviewPath"></ion-img>
          </ion-col>
        </ion-row>
      </ion-grid>

      <ion-fab vertical="bottom" horizontal="center" slot="fixed">
        <ion-fab-button @click="takePhoto()">
          <ion-icon :icon="camera"></ion-icon>
        </ion-fab-button>
      </ion-fab>
    </ion-content>
  </ion-page>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonFab, IonFabButton, IonIcon, IonGrid, IonRow, IonCol, IonImg } from '@ionic/vue';
import { camera } from "ionicons/icons";
import { userPhotoGallery } from "@/composable/userPhotoGallery";
export default defineComponent({
  name: 'Tab1Page',
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonFab, IonFabButton, IonIcon, IonGrid, IonRow, IonCol, IonImg },
  setup() {
    const { takePhoto, photos } = userPhotoGallery();
    return {
      camera,
      takePhoto,
      photos
    }
  },
});
</script>
