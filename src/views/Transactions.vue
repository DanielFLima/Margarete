<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button default-href="/home"></ion-back-button>
        </ion-buttons>
        <ion-title>Transações</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content>
      <ion-list>
        <ion-item-sliding
          v-for="transaction in transactions"
          :key="transaction.id"
        >
          <ion-item>
            <ion-icon :icon="homeOutline"></ion-icon>
            <ion-label>
              <h2>{{ transaction.description }}</h2>
              <h3>{{ transaction.category }}</h3>
              <h4>{{ transaction.value }}</h4>
            </ion-label>
          </ion-item>

          <ion-item-options side="end">
            <ion-item-option :router-link="`/EditTransaction/${transaction.id}`"
              >Editar</ion-item-option
            >
            <ion-item-option color="danger" @click="Delete(item)"
              >Excluir</ion-item-option
            >
          </ion-item-options>
        </ion-item-sliding>
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script>
import TransactionsData from "./TransactionsData.json";

import { defineComponent } from "vue";
import {
  IonIcon,
  IonLabel,
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonList,
  IonItemSliding,
  IonItemOption,
  IonItemOptions,
  IonContent,
  IonItem,
  IonButtons,
  IonBackButton,
} from "@ionic/vue";
import { homeOutline } from "ionicons/icons";

export default defineComponent({
  name: "TransactionsPage",
  components: {
    IonIcon,
    IonLabel,
    IonPage,
    IonHeader,
    IonToolbar,
    IonTitle,
    IonList,
    IonItemSliding,
    IonItemOption,
    IonItemOptions,
    IonContent,
    IonItem,
    IonButtons,
    IonBackButton,
  },
  setup() {
    return {
      homeOutline,
    };
  },
  data() {
    return {
      transactions: TransactionsData.transactions,
    };
  },
});
</script>

<style scoped>
</style>