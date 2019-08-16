<template>
  <v-container>
    <v-layout column justify-center align-center>
      <v-flex xs12>
        <v-card width="800px" class="elevation-0">
          <v-card-title class="title">
            Profile
          </v-card-title>
          <v-card-text>
            <v-layout wrap>
              <v-flex xs12 sm3>
                <v-img right
                  width="150px"
                  height="150px"
                  :aspect-ratio="2/2"
                  :src="require('../assets/anna.jpg')"
                ></v-img>
              </v-flex>
              <v-flex xs12 sm9>
                <p class="subtitle-1">
                  <p class="subtitle-1">
                  <span>Full Name : </span> <span>Anna Kurniaty</span> <br>
                  <span>Birthplace : </span> <span>Bandung</span> <br>
                  <span>Birthdate : </span> <span>08th March 2002</span>
                </p>
              </v-flex>
            </v-layout>
          </v-card-text>
        </v-card>

        <v-scroll-y-transition>
        <v-card width="800px" class="my-4 elevation-0">
          <v-card-title class="title">
            Hobbies
          </v-card-title>
          <v-card-text>
            <v-layout wrap>
              <template v-for="item in hobbies">
                <v-flex xs12 sm4 :key="item.id">
                  <v-icon>{{item.icon}}</v-icon> &nbsp;
                  <span class="subtitle-2">{{item.title}}</span>
                  <v-tooltip left bottom>
                    <template v-slot:activator="{ on }">
                      <p v-on="on" class="ma-0 text-truncate">
                        <v-rating
                          dense readonly
                          :empty-icon="emptyIcon"
                          :full-icon="fullIcon"
                          :half-icon="halfIcon"
                          :length="item.count"
                          background-color="red lighten-3"
                          half-increments color="red darken-2"
                          v-model="item.rate">
                        </v-rating>
                      </p>
                    </template>
                    <span>{{item.description}}</span>
                  </v-tooltip>
                  <!-- <v-img right
                    width="150px"
                    height="150px"
                    :aspect-ratio="2/2"
                    :src="require('../assets/pas_foto.jpeg')"
                  ></v-img> -->
                </v-flex>
              </template>
            </v-layout>
          </v-card-text>
        </v-card>  
        </v-scroll-y-transition>    

        <v-card width="800px" class="my-4 elevation-0">
          <v-card-title class="title">
            Education
          </v-card-title>
          <v-card-text>
            <v-layout wrap>
              <template v-for="item in educations">
                <v-flex xs12 sm4 :key="item.id" style="padding: 8px 4px">
                  <v-icon>{{item.icon}}</v-icon> &nbsp;
                  <span class="subtitle-2">{{item.title}}</span>
                  <br><br>
                  <!-- <v-img right
                    width="100%"
                    height="150px"
                    style="margin: 8px 0"
                    :aspect-ratio="2/2"
                    :src="require('../assets/pas_foto.jpeg')"
                  ></v-img> -->
                  <iframe :src="item.loc" width="100%" height="100px" frameborder="0" style="border:0" allowfullscreen></iframe>
                  <v-hover>
                    <span 
                      class="subtitle-2"
                      slot-scope="{ hover }" 
                      style="cursor: pointer"
                    >
                      <a :href="item.link" target="_blank" rel="noopener noreferrer">
                        <v-icon :color="`${hover ? 'blue' : 'grey'}`">mdi-map-marker</v-icon> &nbsp;
                        <span  :class="`${hover ? 'textblue' : 'textgrey'}`">
                          {{item.name}}
                        </span>
                      </a>
                    </span>
                  </v-hover>
                </v-flex>
              </template>
            </v-layout>
          </v-card-text>
        </v-card>      

        <v-card width="800px" class="my-4 elevation-0">
          <v-card-title class="title">
            Skills
          </v-card-title>
          <v-card-text>
            <v-list-item v-for="item in skills" :key="item.id" dense>
              <v-list-item-content>
                <v-list-item-title>
                  <!-- <div v-html="item.title"></div> -->
                  {{item.title}}
                </v-list-item-title>
                <v-list-item-subtitle>
                  <v-progress-linear
                    :color="item.color"
                    :background-color="item.bgColor"
                    :length="item.count"
                    v-model="item.rate"
                  ></v-progress-linear>
                </v-list-item-subtitle>
              </v-list-item-content>
              <v-list-item-action>
                {{ item.rate }} / 100
              </v-list-item-action>
            </v-list-item>
          </v-card-text>
        </v-card>
        
        <v-card width="800px" class="my-4 elevation-0">
          <v-card-title class="title">
            Language Skills
          </v-card-title>
          <v-card-text>
            <v-card v-for="item in languages" :key="item.id" flat>
              <v-card-text class="pb-0 subtitle-1">
                <span style="color: black;">{{item.title}}</span>
              </v-card-text>
              <v-card-text class="pt-0">
                <v-layout wrap>
                  <v-flex xs4>
                    <span class="subtitle-4">Writing</span> <br>
                    <v-progress-circular
                      :value="item.score.writing"
                      color="error"
                      size="100"
                      width="15"
                    >{{item.score.writing}}</v-progress-circular>
                  </v-flex>
                  <v-flex xs4>
                    <span class="subtitle-4">Speaking</span> <br>
                    <v-progress-circular
                      :value="item.score.speaking"
                      color="blue"
                      size="100"
                      width="15"
                    >{{item.score.speaking}}</v-progress-circular>
                  </v-flex>
                  <v-flex xs4>
                    <span class="subtitle-4">Reading</span> <br>
                    <v-progress-circular
                      :value="item.score.reading"
                      color="orange"
                      size="100"
                      width="15"
                    >{{item.score.reading}}</v-progress-circular>
                  </v-flex>
                </v-layout>
              </v-card-text>
              <v-divider></v-divider>
            </v-card>
          </v-card-text>
        </v-card>
      </v-flex>

      <v-scroll-y-transition>
        <v-btn
          v-if="goUpButton"
          color="yellow darken-1"
          small
          fixed
          bottom
          right
          fab
          @click="$vuetify.goTo(target, options)"
        >
          <v-icon color="grey darken-4">mdi-gesture-swipe-up</v-icon>
        </v-btn>
      </v-scroll-y-transition>
    </v-layout>
  </v-container>
</template>

<style scoped>
  .textblue{
    color: #2196F3 !important;
  }
  .textgrey{
    color: #9E9E9E !important;
  }

  .v-list-item__content {
    padding: 0px !important;
  }
  
  a{
    text-decoration: none
  }
</style>

<script>
export default {
  data: () => ({
    goUpButton: false,
    hobby: '',
    education: '',
    skill: '',
    language: '',
    
    hobbies: [
        { id: 1, icon: 'mdi-microfon', title:'Singing', count: 5, rate: 3, description: 'I like this so much:v' },
      { id: 2, icon: 'mdi-camera', title:'Photography', count: 5, rate: 4, description: '4/5' },
      { id: 3, icon: 'mdi-code-not-equal-variant', title:'Coding', count: 10, rate: 5.5, description: '5.5/10' },
    ],

    educations: [
        { 
        id: 1, icon: 'mdi-face', title:'Elementary', 
        name: "SDN Tunas Harapan 2",
        loc: 'https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d15842.976188889306!2d107.5690305!3d-6.9211711!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x997a3cb47aa5d1a!2sSD+Negeri+Tunas+Harapan+2!5e0!3m2!1sid!2sid!4v1565911300213!5m2!1sid!2sid', 
        link: 'https://goo.gl/maps/Pi236Wj3hz9MrS6X9'
      },
      { 
        id: 2, icon: 'mdi-school', title:'Middle', 
        name: "SMPN 1 Bandung",
        loc: 'https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d15843.294191318322!2d107.5966265!3d-6.9116905!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x9c9b8e41fb1c75b6!2sSMP+Negeri+1+Bandung!5e0!3m2!1sid!2sid!4v1565910159512!5m2!1sid!2sid', 
        link: 'https://goo.gl/maps/KHVApiEivfK5BN1UA'
      },
      { 
        id: 3, icon: 'mdi-laptop-windows', title:'Vocational', 
        name: "SMKN 11 Bandung",
        loc: 'https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d15843.994999375504!2d107.5583041!3d-6.8907515!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0xf843088e2b5bf838!2sSMK+Negeri+11+Bandung!5e0!3m2!1sid!2sid!4v1565911735901!5m2!1sid!2sid', 
        link: 'https://goo.gl/maps/GFG3H7kTBQjLBbmb6'
      }
    ],

    skills: [
        {
            id: 1, title: 'Photoshop', count: 10, rate: 55,
            color: 'blue', bgColor: 'blue lighten-3',
        },
        {
            id: 2, title: 'Corel Draw', count: 10, rate: 50,
            color: 'green', bgColor: 'green lighten-3',
        },
        {
            id: 3, title: 'Vue Js', count: 10, rate: 45,
            color: 'red', bgColor: 'red lighten-3',
        },
        {
            id: 5, title: 'Code Igniter', count: 10, rate: 75,
            color: 'red lighten-1', bgColor: 'red lighten-3',
        },
        {
            id: 6, title: 'Sony Vegas', count: 10, rate: 80,
            color: 'orange lighten-1', bgColor: 'orange lighten-3',
        }
    ],

    languages: [
      { 
        id: 1, 
        title: 'Bahasa Indonesia', 
        score: {
          writing: 100, speaking: 100, reading: 100
        }
      },
      { 
        id: 2, 
        title: 'Sundanesse', 
        score: {
          writing: 80, speaking: 80, reading: 90
        }
      },
      { 
        id: 3, 
        title: 'English', 
        score: {
          writing: 85, speaking: 95, reading: 90
        }
      },
      { 
        id: 4, 
        title: 'Japanese', 
        score: {
          writing: 75, speaking: 70, reading: 60
        }
      }
    ],

    emptyIcon: 'mdi-heart-outline',
    fullIcon: 'mdi-heart',
    halfIcon: 'mdi-heart-half-full',

    scrollPosition: 0,
  }),

  mounted() {
    window.onscroll = () => {
      this.scrollPosition = document.documentElement.scrollTop
      if (document.documentElement.scrollTop > 300) {
        this.goUpButton = true  
        // console.log(this.scrollPosition);
        
        
        // document.getElementById("goUp").style.display = 'block'   
      } else {
        this.goUpButton = false
        // document.getElementById("goUp").style.display = 'none'
      }
    }
  },

  computed: {
    target () {
      const value = 0
      return value
    },
    options () {
      return {
        duration: 1000,
        offset: 0,
        easing: 'easeInOutCubic'
      }
    },
  },

  methods: {
    goUp() {
      document.documentElement.scrollTop = 0;
    },
  },
};
</script>
