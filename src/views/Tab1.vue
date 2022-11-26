<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Meu Perfil</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Meu Perfil</ion-title>
        </ion-toolbar>
      </ion-header>

      <img id="foto_de_perfil" :src="user.imagem" />

      <h3 id="nome_de_usuario">{{ user.nome }}</h3>

      <p id="bio_de_usuario">{{ user.bio }}</p>

      <!-- <h3 id="nome_de_usuario">GzuiXYZ</h3> https://www.collinsdictionary.com/images/full/fox_104612975.jpg

      <p id="bio_de_usuario">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua.
      </p> -->
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
} from "@ionic/vue";

import { ref } from "vue";
import axios from "axios";

export default {
  name: "Perfil",
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage },
  setup() {

    

    const user = ref({
      imagem: ``,
      nome: ``,
      bio: ``,
    });

    axios.get("https://vue-tabs-33949-default-rtdb.firebaseio.com/user/.json");
    .them({{data}}=>  
      console.log(data);
    });
    

    return {
      user,
    };
  },
};
</script>

<style scoped>
ion-content {
  text-align: center;
}

#foto_de_perfil {
  aspect-ratio: auto;
  object-fit: none;
  object-position: -140px 0px;
  width: 200px;
  height: 200px;
  border-radius: 50%;
}

#nome_de_usuario {
  color: purple;
}

#bio_de_usuario {
  width: 250px;
  margin: 3em auto;
}
</style>