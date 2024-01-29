# TOS_Nuxt_Add_Component

Bonjour,
<br/> Le but de ce TOS est de vous apprendre à implémenter des composants dans une page nuxtjs3.

Prérequis : 
<br/> Node.js installé : https://nodejs.org/en/download

## 1.
Ouvrez votre terminal et exécutez la commande suivante pour créer un nouveau projet Nuxt.js :
```
npx create-nuxt-app nom-du-projet
```
------------------------------------------------------------------------------------------------------------------------------

## 2.
Créez un répertoire pour les composants de votre projet.
<br/> Les composants sont généralement placés dans le répertoire components à la racine du projet.

------------------------------------------------------------------------------------------------------------------------------

## 3.
Allez dans le répertoire components et créez un nouveau fichier pour votre composant (par exemple: Header.vue).
</br> Pour notre exemple, le composant contient un bouton qui redirige vers la page home et le titre de la page.
```
<template>
  <div>
    <v-btn to="/home">
      <v-icon>mdi mdi-home</v-icon>
    </v-btn>
    <h1> Titre de la page </h1>
  </div>
</template>

<script>
/* scripts spécifiques au composant ici */
</script>

<style scoped>
/* Styles spécifiques au composant ici */
</style>
```
------------------------------------------------------------------------------------------------------------------------------

## 4.
Allez dans le répertoire pages et ouvrez la page où vous souhaitez utiliser le composant.
<br/> Intégrez le composant dans votre page :
```
<template>
  <div>
    <Header titre="Titre de la page"/>
  </div>
</template>

<script setup>
import Header from '../components/Header.vue'
</script>
```

------------------------------------------------------------------------------------------------------------------------------

## 5.
Vous pouvez personnaliser les propriétés du composant en passant des valeurs différentes pour les props. 
<br/> Dans l'exemple ci-dessus, nous avons défini titre comme propriété que vous pouvez passer depuis la page parente.
```
<template>
  <div>
    <v-btn to="/home">
      <v-icon>mdi mdi-home</v-icon>
    </v-btn>
    <h1>{{ titre }}</h1>
  </div>
</template>

<script>
export default {
  props: {
    titre: String
  }
};
</script>

<style scoped>
/* Styles spécifiques au composant ici */
</style>
```

------------------------------------------------------------------------------------------------------------------------------

## 6.
Si vous souhaitez que ce composant soit présent dans toutes les pages, je vous recommande de l'importer dans un layout.
<br/> Pour cela, allez dans le répertoire layouts, ouvrez le layout default et importez le composant. 
```
<template>
    <div>
        <v-app>
            <Header/>
            <v-main id="containerPage">
                <v-container class="pa-0" fluid>
                    <slot />
                </v-container>
            </v-main>    
        </v-app>
    </div>
</template>

<script setup>
import Header from '../components/Header.vue'
</script>

<style scoped>
/* Styles spécifiques au composant ici */
</style>
```

------------------------------------------------------------------------------------------------------------------------------

## 7.
Retournez dans le terminal et exécutez la commande suivante pour démarrez votre application Nuxt.js :
```
npm run dev
```

Et voila ! 
<br/>Votre composant est créé et importé dans votre page. Vous pouvez aussi importer des composants depuis des librairy.
Pour plus d'informations, je vous renvoie vers la documentation nuxtj3 : 
<br/>
https://nuxt.com/docs/guide/directory-structure/components
