<template>
  <div>
  <h2 id="maaain">Here's My Opensource Work.</h2>
    <v-alert error v-bind:value="showErr" icon="new_releases">
      There's been an Issue with Connectivity, due to which We can't load OpenSource Repostiories. Please Try again Later.
    </v-alert>
    <br />
  <div class="v2"  v-for="repo in repos">
  	<h4>{{repo.name}}</h4>
	<p>{{repo.description}}</p>
	<a :href="repo.html_url" target="_blank" class="btn">Open Repository</a>
  </div>
  </div>
</template>

<script>
export default {
  name: 'work',
  data () {
    return {
        showErr: false,
        repos: [],
        api: {
          repos: 'https://api.github.com/users/DakshMiglani/repos?per_page=100&page=',
          user: 'https://api.github.com/users/DakshMiglani'
        }
    }
  },
  methods: {
    openLink: (l) => {
      window.open(l, '_blank')
    },
    getUser: function() {
      this.$http.get(this.api.user).then(function(data) {
        if(data.body.public_repos < 100) {
          this.getRepos(1)
        } else {
          this.getRepos(Math.round(data.body.public_repos / 100))
        }
      }, function(err) {
        this.showErr = true
      })
    },
    getRepos: function(p) {
      for(let i = 0; i < p; i++) {
        this.$http.get(this.api.repos+i).then(function(data) {
          for(var j = 0; j < data.body.length; j++) {
            if(data.body[j].fork !== true) {
              this.repos.push(data.body[j])
            }
          }
        }, function(err) {
          this.showErr = true
        })
      }
    }
  },
  created() {
    this.getUser()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #maaain {
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
    text-align: center;
    margin-bottom: 45px;
  }
  @media (max-width: 576px) {
    .v2 {
      width: 90vw;
    }
    #maaain {
      font-size: 25px;
    }
  }
</style>
