<template>
  <div>
  <h2>About, Me.</h2>
  <div class="v2">
<p>Hi, I'm Daksh; I am a 15 year old, who loves to program. I was 8 when I got my first computer, and certainly I was lucky to be one from those families who can afford a Computer in those old times especially in India, People mostly live in poverty here.</p> <p>Leaving that aside, I was fascinated by computers and how the components of the computers worked. I wanted to know more about them, I spent most of my daily time on it. If I Speak in Layman's terms, I loved Computers and I always wanted to do something related to them, So I started Programming when I was 10.</p> <p>My Parents weren't happy due to that, They tried to shape me into a sportsperson and tried separating me from the family by sending me to Boarding school, But you know I loved computers. So It didn't matter, I came back and enjoyed it.</p> <p>After that, the phase of my life changed. I learnt new things and started making money out of it and my parents were actually impressed and convinced that I could do something in life. So they started being supportive and to be honest, my dad was always supporting me, I don't know about my mom, you know typical Indian Mom's.</p> <p>As the phase changed, I became more interested in Science (especially cosmology) as well. To be honest, the only subject I ever loved except computer science was Science, Cause you get to know about yourself and how the world works in the real way. So I became a Science Fnatic, Made some tools to support my love for Cosmos.</p> <p>Now, I didn't expect this to happen; But now I find myself interested in machine learning and AI which is a field of Computer Science and requires prior knowledge of advance math equations and science, Hence I Chose Physics, Chemistry, Mathematics and Computer Science as my Subjects in my current grade (11th)</p> <p>I would like to end here, by saying just a single sentence. <br>
        "Whatever you do in life, Love it and Enjoy working on it because at the end of the day, You did what you loved and there's no complaining."</p>
  </div>
  </div>
</template>

<script>
export default {
  name: 'home',
  data () {
    return {
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
  h2 {
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
  }
  .ico {
     margin-right:5%;
  }
  .v3 {
    text-align: center;
    align-items: center;
  }
</style>
