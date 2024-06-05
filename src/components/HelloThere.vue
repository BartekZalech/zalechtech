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

    <article class="short-about">

      <h2 class="short-about__text">Tworzę nowoczesne<br>
      <span class="text-stroke">strony internetowe</span><br>
      które wzniosą Twój<br>
      <span class="text-stroke">biznes na wyższy poziom</span></h2>
      <div class="socials">
        <a class="socials__links" target="_blank" :href="github"> <img src="./../assets/github.svg" alt="github" class=""/></a>
        <a class="socials__links" target="_blank" :href="linkedin"> <img src="./../assets/linkedin.svg" alt="linkedin" class=""/></a>
      </div>
    </article>
    <div class="avatar-warpper">
      <img src="./../assets/me.jpg" alt="" class="round image-avatar">
      <VueWriter :typeSpeed="100" :caret="cursor" :eraseSpeed="50" :delay="600" :array="experience" />

      <h1>Developer</h1>
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
  margin-left: 30px;
  margin-right: 30px;
}
.about-me{
  min-height: 100vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 1000px;

}
.about-me .socials{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-start;
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


.avatar-warpper{
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1.light-big {
  font-size: 2em;
  font-weight: lighter;
}

img.round {
  border-radius: 50%;
}
.image-avatar{
  margin-bottom: .5rem;
  /* flex-basis: 50%; */
}
.short-about{
  /* text-align: center; */
  /* flex-basis: 50%; */
  width: 100%;
}
.short-about .short-about__text{
  text-transform: uppercase;
  font-weight: bold;
  font-family: 'Poppins', sans-serif;
  font-size: 2.4rem;

}
.short-about .is-typed{
  font-size: 3rem;
}
.is-typed .typed{
  /* background: linear-gradient(-0.25turn, #83ecec, #fab1a0);
  background-size: 200% 200%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  -webkit-text-stroke-width: 1px;
  -webkit-text-stroke-color: #000;
  -webkit-text-stroke: 8px transparent; */
  font-size: 2.4rem;
  /* font-weight: bold; */
}
.text-stroke{
  -webkit-text-stroke: 1px #000;
  color: transparent;
  background-clip: text;

}
/* .short-about .is-typed .typed::after{
  content: ".";
} */
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




@media only screen and (min-width: 768px) {
  h1.light-big {
    font-size: 3em;
  }
  .about-me{
    flex-direction: row;
  }
}</style>
