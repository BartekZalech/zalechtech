<script>
export default {
  name: 'Technologies',
  data() {
    return {
      posts: [],
      // isLoading: false,
    };
  },
  methods: {

    async fetchPosts() {
      this.isLoading = true;

      const response = fetch('https://panel.zalechtech.pl/wp-json/wp/v2/pages/72')

        .then((response) => response.json())

        .then((data) => {
          // console.log(data);
          this.posts = data.acf;
          console.log( data.acf );

          // this.isLoading = false;
        });
    },


  },

  mounted() {

    this.fetchPosts();

  },
}
</script>

<template>
  <div class="container-fluid">

    <div class="tech-wrapper">
    <h1 class="light-big text-center">Technologie:</h1>



      <!-- <p v-if="isLoading">Loading...</p> -->
      <ul class="tech-list" >
        <li class="tech-item" v-for="p in posts.technologies " :key="p.id">

          {{ p.tech.name }}




        </li>

      </ul>



    </div>

  </div>

</template>



<style>


.tech-wrapper{
  justify-content: center;
  vertical-align: middle;
  flex-direction: row;
  flex-wrap: wrap;
  display: flex;
  margin: auto;
  margin-top: 75px;
  margin-bottom: 75px;
  max-width: 600px;
}

.tech-list{
  display: flex;
  justify-content: center;
	align-items: center;
  list-style: none;
  width: 100%;
  margin-top: 25px;
  margin-bottom: 15px;
  padding: 0;
  flex-direction: row;
  flex-wrap: wrap;
}
.tech-list .tech-item{
  border: 1px solid #2c3e50;
  padding: 5px 8px;
  border-radius: 5px;
  margin-bottom: 1rem;
  margin-right: 1rem;
  /* background: linear-gradient(-0.25turn, #83ecec, #fab1a0); */


}


</style>