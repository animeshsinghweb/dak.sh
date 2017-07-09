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
          user: 'https://api.github.com/users/DakshMiglani',
          repos: 'https://api.github.com/users/DakshMiglani/repos?per_page=100&page='
        }
    }
  },
  methods: {
    openLink: (l) => {
      window.open(l, '_blank')
    },
    getUsers: () => {
      this.$http.get(this.api.users).then((data) => {
        if(data.public_repos > 100) {
          this.getRepos(1)
        } else {
          this.getRepos(Math.round(data.public_repos / 100))
        }
      }, (err) => {
        this.showErr = true
      })
    },
    getRepos: (pageNumber) => {
      for(let i = 0; i < pageNumber; i++) {
        this.$http.get(this.api.repos+i).then((data) => {
          
          for(var j in data.body) {
            if(data.body[j].fork !== true) {
              this.repos.push(data.body[j])
            }
          }
        }, (err) => {
          this.showErr = true
        })
      }
    }
  },
  created() {
    this.getRepos()
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
