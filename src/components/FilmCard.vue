<template>
  <div class="film-card">
    <img
      :src="'https://image.tmdb.org/t/p/w300' + film.backdrop_path"

      :alt="film.title"
    >
    <p class="rating">{{ film.popularity }}</p>
    <p class="title">{{ film.title }}</p>
    <div class="film-counter">
      <Counter 
      :film="film"
      />
    </div>
    <router-link :to="{ name: 'filmPage', params: { id: film.id } }"
      class="more-info"
    >
      Подробнее о фильме
    </router-link>
  </div>
</template>

<script>
import Counter from '../components/Counter'
export default {
  data(){
    return {
      count: 4
    }
  },
  props: {
    film: {
      type: Object
    }
  },
  components: {
    Counter
  }
}
</script>

<style scoped>
.film-card {
  position: relative;
  width: 700px;
  margin: 0 auto;
}
.film-card img {
object-fit: cover;
border-radius: 10px;
width: 100%;
height: auto;
}
.film-card .title {
position: absolute;
margin-bottom: 0;
bottom: 0;
left: 0;
width: 100%;
color: #ffffff;
height: 100px;
background: linear-gradient(90deg, rgba(0,0,0,1) 0%, rgba(0,0,0,0) 90%);
font-weight: 700;
padding: 20px;
font-size: 30px;
border-radius: 0 0 10px 10px;
}

.film-card .film-counter{
  position: absolute;
  right: 30px;
  bottom: 30px;
  z-index: 5;
}

.film-card .rating {
position: absolute;
right: 0;
top: 0;
background-color: #EB5804;
width: 100px;
height: 50px;
margin-bottom: 0;
display: flex;
justify-content: center;
align-items: center;
color: #ffffff;
font-weight: 700;
font-size: 20px;
border-radius: 0 10px 0 10px;
opacity: 0.8;
}
.film-card .more-info {
position: absolute;
top: 0;
left: 0;
bottom: 0;
right: 0;
border-radius: 10px;
background-color: rgba(0, 0, 0, 0.6);
color: #ffffff;
display: flex;
justify-content: center;
align-items: center;
font-weight: 700;
font-size: 30px;
text-decoration: none;
opacity: 0;
transition: all 0.2s ease;
}

.more-info:hover, .more-info:focus {
    opacity: 1;
}
</style>
