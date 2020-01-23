<template>
  <div class="container">
    <div v-for="movie in movies" :key="movie._id">
      <div class="movie__container">
        <h2>{{movie.title}}</h2>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      movies: []
    }
  },
  mounted() {
    const query = '*[_type == "movie"]'
    this.$sanity.fetch(query).then(result => {
      this.movies = result
    })
  }
}
</script>

<style lang="scss">
.container {
  display: grid;
  grid-template-columns: repeat(auto-fill, 300px);
  gap: 20px;
  padding: 20px;
}

.movie__container {
  border: 1px solid gray;
  border-radius: 10px;
  height: 300px;
  width: 300px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding: 20px;

  h2 {
    font-size: 24px;
  }
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
</style>
