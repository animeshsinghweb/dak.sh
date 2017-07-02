<template>
  <div>
  <h2 id="mainh">Hello, I'm Daksh.</h2>
  <div class="v2">
    <p>I'm a 15 Year Old Wizard, Who uses Python-JavaScript and C++ for Magic. I'm also a Deep-Learning Student and a Space Enthusaist.</p>
  </div>
  <div class="v3">
     <v-icon medium fa dark class="ico" v-for="(item, i) in items" :key="i" @click="openLink(item.url)">{{item.name}}</v-icon>
  </div>
  </div>
</template>

<script>
export default {
  name: 'home',
  data () {
    return {
      items: [
        {
          name: 'github',
          url: 'https://github.com/DakshMiglani'
        },
        {
          name: 'facebook',
          url: 'https://facebook.com/DakshMTGV'
        },
        {
          name: 'twitter',
          url: 'https://twitter.com/Dak_ssh'
        },
        {
          name: 'instagram',
          url: 'https://instagram.com/DakshMiglani'
        },
        {
          name: 'medium',
          url: 'https://medium.com/@dak.sh'
        },
      ]
    }
  },
  methods: {
    openLink: (l) => {
      window.open(l, '_blank')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  #mainh {
    color: #263238 !important;
    font-size: 50px;
    text-align: center;
  }
  p {
    text-align: center;
    font-size: 20px;
  }
  .v2 {
    width: 50vw;
  }
  @media (max-width: 576px) {
    .v2 {
      width: 90vw;
    }
    #mainh {
      font-size: 40px
    }
  }
  .ico {
     margin-right:5%;
  }
  .v3 {
    text-align: center;
    align-items: center;
  }
</style>
