<template>
  <q-page class="row items-center justify-evenly text-brand">
    <q-form
      class="column q-px-xl q-py-md shadow-2 bg-blue-1"
      action=""
      method=""
    >
      <q-input 
        v-model="form.title" 
        name="title" 
        placeholder="Movie Title"
        :rules="[requireVal]" />
      <q-input v-model="form.movieId" name="movieId" placeholder="Movie Id" />
      <p class="q-mt-lg q-mb-none text-grey ">Released Date</p>
      <q-input
        class="q-mt-none"
        v-model="form.released"
        type="date"
        name="year"
        
        :rules="[requireVal]"
      />
      <q-input
        v-model="form.runtime"
        type="text"
        name="runtime"
        placeholder="Runtime"
        :rules="[requireVal]"
      />
      <q-input
        v-model="form.rated"
        type="text"
        name="rated"
        placeholder="Rated"
        :rules="[requireVal]"
      />
      <q-input
        v-model="form.imdbRating"
        type="number"
        name="imdbRating"
        placeholder="imdbRating"
        :rules="[requireVal]"
      />
      <q-input
        v-model="form.rTRating"
        type="text"
        name="rTRating"
        placeholder="Rotten Tomato Rating"
        :rules="[requireVal]"
      />
      <q-file
        class="q-mt-md"
        outlined
        v-model="form.posterLink"
        name="cinemaPosterURL"
        label="Attach Poster Image"
        accept="image/*"
        :rules="[requireVal]"
      >
        <template v-slot:prepend>
          <q-icon name="attach_file" />
        </template>
      </q-file>

      <q-btn 
        @click="submitForm" 
        class="q-mt-xl" 
        label="Add Movie" 
        type="submit" 
        color="green"
        :disabled="isFormValid" />
    </q-form>

    <q-table
      title="Movie List"
      :rows="movies"
      :columns="columns"
      row-key="name"
      :loading="loading"
    />
  </q-page>
</template>

<script setup>

import { ref } from 'vue';

const form = ref({
  title: '',
  movieId: '',
  rated: '',
  released: '',
  runtime: '',
  imdbRating: null,
  rTRating: '',
  
});

const requireVal = val => !!val || 'Invalid Input'



const movies = [
  {
    title: 'Doctor Strange in the Multiverse of Madness',
    movieId: 'movie1',
    year: 2022,
    rated: 'PG-13',
    released: '18 Dec 2022',
    runtime: '2h 6m',
    imdbRating: 6.9,
    rTRating: '74%',
    posterLink: 'doctor.png',
  },
  {
    title: 'The Bad Guys',
    movieId: 'movie2',
    year: 2022,
    rated: 'PG',
    released: '22 April 2022',
    runtime: '1h 40m',
    imdbRating: 6.8,
    rTRating: '62%',
    posterLink: 'bad.png',
  },

];

const columns = [
  { name: 'Title', field: 'title', align: 'left', label: 'Title' },
  { name: 'Year', field: 'year', label: 'Released Year' },
  { name: 'Rated', field: 'rated', label: 'Rated' },
  { name: 'Released', field: 'released', label: 'Released Date' },
  { name: 'Runtime', field: 'runtime', label: 'Runtime' },
  { name: 'IMDb Rating', field: 'imdbRating', label: 'IMDB Rating' },
  { name: 'Rotten Tomatoes Rating', field: 'rTRating', label: 'RT Rating' },
  { name: 'Type', field: 'type', label: 'Type' },
];

const loading = false;

console.log(form.value)

const isFormValid = () =>{
  for(const key of form.value){
    if(form.value[key] !== null && form.value[key] !== '' ){
       return false
    }
  } return true
    
}

const submitForm = e => {
  e.preventDefault();
  movies.unshift({
    title: form.value.title,
    movieId: form.value.movieId,
    year: parseInt(form.value.released.slice(0,4)) ,
    rated: form.value.rated ,
    released: form.value.released ,
    runtime: form.value.runtime ,
    imdbRating: form.value.imdbRating ,
    rTRating: form.value.rTRating ,
    posterLink: form.value.posterLink ,
  });
 
}




</script>
