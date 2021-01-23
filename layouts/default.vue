<template>
  <v-app>
    <!-- Header  -->
    <v-toolbar
      color="black" 
    >   
        <v-col cols="6" sm="6" md="4" lg="3">
          <v-toolbar-items>
          <v-text-field 
            v-model="movieinput"
            class="pt-6"
            label="Search Movie"
            background-color="white"
            color="black"
            append-icon="mdi-magnify"
            @click:append="searchmovie"
            outlined            
            clearable
            rounded
            >
          </v-text-field>
          </v-toolbar-items>
        </v-col>
      <v-spacer />
      <!-- Bar Left  -->
      <v-menu
        bottom
        left
        >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            class="hidden-md-and-up"
            icon
            v-bind="attrs"
            v-on="on"
            color="white"
            >
            <v-icon>mdi-menu</v-icon>
          </v-btn>
        </template>
        <v-list>
          <v-list-item
            v-for="(item,i) in listnavegation"
            :key="i"
            >
            <v-btn 
              text
              color="info"
              nuxt
              :to="item.navegationto"
            >
              {{item.title}}
            </v-btn>
          </v-list-item>
        </v-list>
      </v-menu>
      <v-toolbar-items v-if="menutop"  
        class="hidden-sm-and-down">
        <v-btn 
          v-for="(item,i) in listnavegation"
          :key="i"
          text
          color="info"
          nuxt
          :to="item.navegationto"
        >
          {{item.title}}
        </v-btn>
        
      </v-toolbar-items>
      <v-btn
        icon
        class="hidden-sm-and-down"
        @click.stop="menutop = !menutop"
        color="white"
      >
        <v-icon>mdi-{{ `chevron-${menutop ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
    </v-toolbar >
    <!-- Content  -->
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <!-- footer -->
    <v-footer
      app
      dark
      :padless= true
    >
      <v-card
        flat
        tile
        width="100%"
        class="text-center"
      >
        <v-card-text class="white--text">
          <span>Copy right &copy; {{ new Date().getFullYear() }}, Andres Echavarria</span>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      menutop: true,
      movieinput: "",
      menudwon: false,
      listnavegation:[
        {title:"Popular",navegationto:"popular"},
        {title:"Top Rated",navegationto:"toprated"},
        {title:"Upcoming",navegationto:"upcoming"}
      ],
    }
  },
  methods:{
    searchmovie(){
      console.log("oprimio search");
    }
  }
}
</script>
