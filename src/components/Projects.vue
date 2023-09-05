<script>


export default {

  data() {
    return {
      post: [],
      isLoading: false,

    };
  },
  methods: {
    getPosts() {
      this.isLoading = true;
      // fetch('https://panel.zalechtech.pl/wp-json/wp/v2/posts') //blog posts
      fetch('https://panel.zalechtech.pl/wp-json/wp/v2/project')
        .then((response) => response.json())
        .then((data) => {
          this.post = data;
          this.isLoading = false;
          this.fetchFeaturedMedia();
          // console.log(data);

        });
    },
    async fetchFeaturedMedia() {
      try {
        for (const post of this.post) {
          if (post._links['wp:featuredmedia']) {
            const mediaResponse = await fetch(post._links['wp:featuredmedia'][0].href);
            const mediaData = await mediaResponse.json();
            post.featuredMedia = mediaData;
          } else {
            post.featuredMedia = null;
          }
        }
      } catch (error) {
        console.error(error);
      }
    },
    getFeaturedMediaUrl(post) {
      if (post.featuredMedia && post.featuredMedia.source_url) {
        return post.featuredMedia.source_url;
      } else {
        return '';
      }
    }
  },

  mounted() {
    this.getPosts();
  },
};
</script>

<template>
  <div class="container">
    <div class="projects">
      <h2 class="projects__header text-center">Realizacje:</h2>
      <p v-if="isLoading">Loading...</p>
      <ul class="project-list">
        <li class="project" v-for="p in post" :key="p.id">
          <a class="project__link" target="_blank" :href="p.acf.project_url">

            <!-- <h3 class="project__title">{{ p.title.rendered }}</h3> -->
            <div class="project__image">
              <div class="project__hover">
                <img src="./../assets/external_link.svg" alt="link icon" class="project__external-link"/>
                <p class="project__external-url">{{ p.title.rendered }}</p>
                <p class="project__tech">{{ p.acf.tech_stack }}</p>
              </div>
              <img  class="img-resp " :src="getFeaturedMediaUrl(p)" alt="{{ p.title.rendered }}">

            </div>
          </a>

        </li>

      </ul>

    </div>
  </div>
</template>

<style>
.projects {
  max-width: 1380px;
  margin-top: 50px;
  margin-bottom: 2rem;
}
.projects__header{
  font-size: 3rem;
  margin-bottom: 2rem;
}
.project-list {
  list-style: none;
  display: grid;
  padding: 0;
  /* Two equal-width columns */
  grid-gap: 20px;
  grid-template-columns: 1fr;


}

.project {
  margin-bottom: 3rem;
  margin-right: 15px;
  margin-left: 15px;
  cursor: pointer;
  box-shadow: rgba(217,217,226,.4);

}
.project__title{
  font-size: 2rem;
  margin-bottom: .5rem;
}
.project__tech{
  margin-bottom: 1rem;
  color: #fff;
  /* position: absolute; */
  /* bottom: 1rem; */
}
.project__link{
  text-decoration: none;
  color: var(--color-text);
}
.project__thumbnail{
  width: 100%;

}
.project__image{
  position: relative;
  border-radius: 10px;
  overflow: hidden;
}
.project__hover{
  position: absolute;
  z-index: 1;
  top: 60%;
  display: flex;
  justify-self: center;
  flex-direction: column;
  align-items: center;
  left: 50%;
  transform: translate(-50%, -50%);
  transition: all .35s;

  opacity: 0;

}
.project__external-link{
  width: 24px;
  height: 24px;

}
.project__external-url{
  color: #fff;
  /* font-weight: bold; */
  font-size: 2rem;
}
.project__image::after{
  transition: all .35s;

  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
  opacity: 0;
  /* background-color: 83ecec */
  background: linear-gradient(-0.25turn, #83ecec, #fab1a0);

}
.project__image:hover::after{
  opacity: .85;

}
.project__image:hover .project__hover{
  opacity: 1;
  top: 50%;



}
@media (min-width: 1024px) {
.project-list {
  grid-template-columns: 1fr 1fr;

}

}

</style>
