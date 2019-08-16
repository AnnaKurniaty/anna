<template>
  <v-app style="background: #ECEFF1">
    <v-app-bar app dark>
      <v-toolbar-title class="Title text-sentencecase">
        <span class="font-weight-bold" style="color: #FDD835">Curriculum</span>
        <span class="font-weight-light" style="color: #FDD835">Vitae</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn dark icon @click="drawer = !drawer">
        <v-icon color="yellow darken-1">mdi-contacts</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer 
      clipped
      temporary
      app
      v-model="drawer"
      fixed class="elevation-0"
    >
      <v-card flat>
        <v-card-text class="pb-0">
            <!-- max-height="150px" -->
          <v-avatar width="220" height="auto">
            <v-img 
              avatar
              :aspect-ratio="2/2"
              :src="require('../src/assets/anna.jpg')"
            ></v-img>
          </v-avatar>
        </v-card-text>
      </v-card>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            Anna Kurniaty <v-icon color="blue lighten-2">mdi-check-decagram</v-icon>
          </v-list-item-title>
          <v-list-item-subtitle>
            Siswa SMKN 11 Bandung
          </v-list-item-subtitle>
          <v-list-item-subtitle>
            annakuykuy25@gmail.com
          </v-list-item-subtitle>
          <v-list-item-subtitle>
            annakrnt25@gmail.com
          </v-list-item-subtitle>
          <v-list-item-subtitle>
            (+62) 882 1874 1877
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          link :href="item.to" target="_blank"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-content>
      <CoreView/>
      <v-container>
      </v-container>
    </v-content>

    <v-footer style="height: 40px; color: #FDD835" dark inset fixed>
      Made with &nbsp;<v-icon small color="green">mdi-vuejs</v-icon>&nbsp; + &nbsp;<v-icon small color="blue">mdi-vuetify</v-icon>&nbsp; = &nbsp;<v-icon small color="red">mdi-heart</v-icon>&nbsp;
    </v-footer>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',
  components: {
    // HelloWorld,
    CoreView: () => import('@/components/View')  
  },
  
  data: () => ({
    drawer: false,
    items: [
      { icon: 'mdi-instagram', text: 'Instagram', to: 'https://www.instagram.com/annakrnt25/'},
      { icon: 'mdi-facebook', text: 'Facebook', to: 'https://www.facebook.com/annakuykuy'},
      { icon: 'mdi-pintrest', text: 'Pinterest', to: 'https://id.pinterest.com/annakuykuy25/'},
      { icon: 'mdi-youtube', text: 'Youtube', to: 'https://www.youtube.com/channel/UCmDSelygm18IhH8Y8JxiE1w?view_as=subscriber'},
    ]
  }),
};
</script>
