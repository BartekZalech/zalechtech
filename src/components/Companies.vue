<script>
export default {
  name: 'Companies',
  data() {
    return {
      posts: [],
      // isLoading: false,
    };
  },
  methods: {

    async fetchPosts() {
      this.isLoading = true;
      const response = fetch('https://panel.zalechtech.pl/wp-json/wp/v2/company')

        .then((response) => response.json())
        .then((data) => {
          // console.log(data);
          this.posts = data;
          this.fetchFeaturedMedia();

          // this.isLoading = false;
        });
    },

    async fetchFeaturedMedia() {
      try {
        for (const post of this.posts) {
          const mediaResponse = await fetch(post._links['wp:featuredmedia'][0].href);
          const mediaData = await mediaResponse.json();
          post.featuredMedia = mediaData;
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

    this.fetchPosts();

  },
}
</script>

<template>
  <div class="container-fluid">

    <div class="company-wrapper">
    <h1 class="light-big text-center">Jestem dumny ze współpracy z niesamowitymi firmami:</h1>



      <!-- <p v-if="isLoading">Loading...</p> -->
      <ul class="companies-list" >
        <li v-for="p in posts " :key="p.id">

            <!-- {{ p.title.rendered }} -->
            <img   :src="getFeaturedMediaUrl(p)" alt="{{ p.title.rendered }}">



        </li>

      </ul>



    </div>

  </div>

</template>



<style>


.company-wrapper{
  justify-content: center;
  vertical-align: middle;
  flex-direction: row;
  flex-wrap: wrap;
  display: flex;
  margin-top: 75px;
  margin-bottom: 75px;
}

.companies-list{
  display: flex;
  justify-content: center;
	align-items: center;
  list-style: none;
  width: 100%;
  margin-top: 25px;
  margin-bottom: 15px;
  padding: 0;
  flex-direction: column;
}
.companies-list img{
  max-width: 200px;
	max-height: 80px;
	display: block;
	width: 100%;
	height: auto;
	padding-left: 25px;
	padding-right: 25px;
}
.companies-list li:not(:last-of-type){
  margin-bottom: 3rem;
  margin-right: 0;
}
@media (min-width: 764px) {
  .companies-list{
    flex-direction: row;
  }
  .companies-list li:not(:last-of-type){
  margin-right: 20px;
  margin-bottom: 0;
}
}
</style>