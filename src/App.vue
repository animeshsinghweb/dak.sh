<template>
  <v-app>
    <v-navigation-drawer
      persistent
      :clipped="clipped"
      v-model="drawer"
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          @click="openLink(item.link)">
          <v-list-tile value="true">
            <v-list-tile-action>
              <v-icon light v-html="item.icon" class="beWhite"></v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title v-text="item.title"></v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar>
      <v-toolbar-side-icon @click.native.stop="drawer = !drawer" light></v-toolbar-side-icon>
      <v-toolbar-title v-text="title" class="beWhite"></v-toolbar-title>
      <v-spacer></v-spacer>
    </v-toolbar>
    <main>
      <v-container fluid>
        <v-slide-y-transition mode="out-in">
          <v-layout column align-center>
            <img src="/static/v.png" alt="Vuetify.js" class="mb-5" />
            <router-view></router-view>
          </v-layout>
        </v-slide-y-transition>
      </v-container>
    </main>
    <v-footer :fixed="fixed">
      <span>&copy; 2017 Daksh Miglani</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        clipped: false,
        drawer: true,
        fixed: false,
        items: [
          { icon: 'home', title: 'Home', link: '/' },
          { icon: 'info', title: 'About', link: '/about' },
          { icon: 'bubble_chart', title: 'Blog', link: 'https://blog.dak.sh' },
          { icon: 'gavel', title: 'Work', link: '/work' },
          { icon: 'widgets', title: 'Download CV', link: '/assets/daksh_cv.pdf' }
        ],
        right: true,
        title: 'Daksh Miglani'
      }
    },
    methods: {
        openLink: function(link) {
          window.location = link
        }
    }
  }
</script>

<style lang="stylus">
  @import './stylus/main'
  img
    border-radius 50%;
    width 19%;
  @media (max-width: 576px)
    img
      width: 40%;

  .beWhite
    color #fff !important
</style>
