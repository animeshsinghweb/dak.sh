<template>
  <div>
    <h2>My Programming Tools -</h2>
    <v-alert error v-bind:value="showErr" icon="new_releases">
      There's been an Issue with Connectivity, due to which We can't load Daksh's Tools yet. Please Try again Later.
    </v-alert>
    <v-container fluid grid-list-xl>
      <v-layout row wrap>
        <v-flex xs4 v-for="n in options" :key="n" style="text-align: center;">
          <a :href="n.link" target="_blank">
          <v-card flat tile>
            <img :src="n.icon" class="images">
            <v-card-title primary-title style="display: block;">
              <div>
                <h3 class="headline mb-0">{{n.name}}</h3>
                <div>
                  {{n.category}}
                </div>
              </div>
            </v-card-title>
            <br />
          </v-card>
          </a>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
export default {
  name:'tools',
  data() {
    return {
      options: [],
      select: [],
      showErr: false
    }
  },
  methods: {
    getTools: function() {
      this.$http.get('/static/tools.json').then(function(data) {
        this.options = data.body
      }, function(err) {
        this.showErr = true
      })
    }
  },
  created() {
    this.getTools()
  }
}
</script>

<style scoped>
.images {
  height: 200px;
  width: 200px;
}
.mb-0 {
  font-size: 150%;
}
a {
  text-decoration:none;
}
</style>
