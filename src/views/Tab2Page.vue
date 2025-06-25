<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Photo gallery</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 2</ion-title>
        </ion-toolbar>
      </ion-header>
    </ion-content>
    <ion-content :fullscreen="true">
      <IonGrid>
        <IonRow>
          <IonCol size="6" v-for="photo in photos" :key="photo.filepath">
            <IonImg :src="photo.webviewPath"></IonImg>
          </IonCol>
        </IonRow>
      </IonGrid>

      <IonFab horizontal="center" vertical="bottom" slot="fixed">
        <IonFabButton @click="takePhoto()">
          <IonIcon :icon="camera"></IonIcon> </IonFabButton
      ></IonFab>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { camera, trash, close } from "ionicons/icons";
import { usePhotoGallery, UserPhoto } from "@/composables/usePhotoGallery";

import {
  IonPage,
  IonHeader,
  IonFab,
  IonFabButton,
  IonIcon,
  IonToolbar,
  IonTitle,
  IonContent,
  IonGrid,
  IonRow,
  IonCol,
  IonImg,
} from "@ionic/vue";
import { onMounted } from "vue";

const { takePhoto, photos } = usePhotoGallery();
onMounted(() => {
  console.info("photos", photos.value);
});
</script>
