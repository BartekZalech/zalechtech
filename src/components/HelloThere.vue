<script>
// import VueTyper from 'vue-typer'

export default {

  data() {
    return {

      title: 'Front-end',

      experience: ['Full stack','Next.js', 'Wordpress', 'Vue.js', 'Grav', 'Web'],
      linkedin: 'https://www.linkedin.com/in/bartlomiej-zalech/',
      github: 'https://github.com/BartekZalech',
    };
  },
  methods: {

  },
};
</script>

<template>
  <div class="container">
    <div class="about-me">

    <img src="./../assets/me.jpg" alt="" class="round image-avatar">
    <article class="short-about">
      <VueWriter :typeSpeed="100" :caret="cursor" :eraseSpeed="50" :delay="600" :array="experience" />
      <h1>developer</h1>
      <p>Witam na mojej stronie.</p>
      <p>Potrzebujesz WWW na najwyższym poziomie?</p>
      <p>Zjedź na dół i zobacz co mogę dla Ciebie zrobić!</p>
    </article>
    <div class="socials">
      <a class="socials__links" target="_blank" :href="github"> <img src="./../assets/github.svg" alt="github" class=""/></a>
      <a class="socials__links" target="_blank" :href="linkedin"> <img src="./../assets/linkedin.svg" alt="linkedin" class=""/></a>
    </div>
  </div>

  </div>

</template>

<style>
@import url('https://fonts.googleapis.com/css?family=Open+Sans+Condensed:300,700&display=swap&subset=latin-ext');

/** { cursor: none; }*/
body {
  margin: 0;
  font-family: 'Open Sans Condensed', sans-serif;
  padding: 0;
}
.container{
  margin: auto;
  display: flex;
  flex-direction: column;
  justify-self: center;
  align-items: center;
}
.about-me{
  min-height: 80vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}
.about-me .socials{
  display: flex;
  flex-direction: row;
  margin: 1.5rem auto;

}
.about-me .socials img{
  width: 24px;
  height: 24px;
}
.about-me .socials .socials__links:not(:last-of-type){
  display: block;
  margin-right: 1rem;

}



h1.light-big {
  font-size: 2em;
  font-weight: lighter;
}

img.round {
  border-radius: 50%;
}
.short-about{
  text-align: center;

}
.short-about .is-typed{
  font-size: 1.5rem;
}

.short-about__title .typed-cursor {
  color: #fab1a0;
}

.text-white {
  color: #fff;
}

.text-center {
  text-align: center;
}

a.custom-link {
  text-decoration: none;
  color: #fab1a0;
  position: relative;
}

a.custom-link:after {
  content: ' ';
  width: calc(100% + 6px);
  position: absolute;
  left: -2px;
  bottom: -5px;
  height: 3px;
  background-color: #fab1a0;
  transition: all .35s;
  z-index: -1;

}

a.custom-link:hover {
  color: #fff;
  transition: all .35s;
}

a.custom-link:hover:after {
  height: 100%;
}


.image-avatar{
  margin-bottom: .5rem;
}

@media only screen and (min-width: 768px) {
  h1.light-big {
    font-size: 3em;
  }
}</style>
