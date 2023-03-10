<template>
  <q-page class="row items-center justify-evenly text-brand">
    <q-form
      class="column q-px-xl q-py-md shadow-2 bg-blue-1"
      action="http://localhost:9000/#/movies"
      method="GET"
    >
      <q-input name="title" placeholder="Movie Title" />
      <q-input name="movieId" placeholder="Movie Id" />
      <q-input type="date" name="year" placeholder="Year Released" />
      <q-input type="text" name="runtime" placeholder="Runtime" />
      <q-input type="number" name="imdbRating" placeholder="imdbRating" />
      <q-input type="text" name="rTRating" placeholder="Rotten Tomato Rating" />
      <q-file
        class="q-mt-md"
        outlined
        v-model="model"
        name="cinemaPosterURL"
        label="Attach Poster Image"
        accept="image/*"
      >
        <template v-slot:prepend>
          <q-icon name="attach_file" />
        </template>
      </q-file>

      <q-btn class="q-mt-xl" label="Add Movie" type="submit" color="green" />
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
    type: 'movie',
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
    type: 'movie',
  },
  {
    title: 'Sonic the HedgeHog 2',
    movieId: 'movie3',
    year: 2022,
    rated: 'PG-13',
    released: '8 April 2022',
    runtime: '2h 2m',
    imdbRating: 6.5,
    rTRating: '64%',
    posterLink: 'sonic.png',
    type: 'movie',
  },
  {
    title: 'Firestarter',
    movieId: 'movie4',
    year: 2022,
    rated: 'R',
    released: '12 May 2022',
    runtime: '1h 34m',
    imdbRating: 4.6,
    rTRating: '55%',
    posterLink: 'firestarter.png',
    type: 'movie',
  },
  {
    title: 'Everything Everywhere All at Once',
    movieId: 'movie5',
    year: 2022,
    rated: 'R',
    released: '8 April 2022',
    runtime: '2h 19m',
    imdbRating: 8.0,
    rTRating: '85%',
    posterLink: 'eeaao.png',
    type: 'movie',
  },
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
    type: 'movie',
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
    type: 'movie',
  },
  {
    title: 'Sonic the HedgeHog 2',
    movieId: 'movie3',
    year: 2022,
    rated: 'PG-13',
    released: '8 April 2022',
    runtime: '2h 2m',
    imdbRating: 6.5,
    rTRating: '64%',
    posterLink: 'sonic.png',
    type: 'movie',
  },
  {
    title: 'Firestarter',
    movieId: 'movie4',
    year: 2022,
    rated: 'R',
    released: '12 May 2022',
    runtime: '1h 34m',
    imdbRating: 4.6,
    rTRating: '55%',
    posterLink: 'firestarter.png',
    type: 'movie',
  },
  {
    title: 'Everything Everywhere All at Once',
    movieId: 'movie5',
    year: 2022,
    rated: 'R',
    released: '8 April 2022',
    runtime: '2h 19m',
    imdbRating: 8.0,
    rTRating: '85%',
    posterLink: 'eeaao.png',
    type: 'movie',
  },
];

const columns = [
  { name: 'Title', field: 'title', align: 'left', label:'Title' },
  { name: 'Year', field: 'year', label:'Released Year' },
  { name: 'Rated', field: 'rated', label:'Rated' },
  { name: 'Released', field: 'released', label:'Released Date' },
  { name: 'Runtime', field: 'runtime', label:'Runtime' },
  { name: 'IMDb Rating', field: 'imdbRating' , label:'IMDB Rating'},
  { name: 'Rotten Tomatoes Rating', field: 'rTRating', label:'RT Rating' },
  { name: 'Type', field: 'type', label:'Type' },
];

// const pagination = {
//   sortBy: 'title',
//   descending: false,
//   page: 1,
//   rowsPerPage: 10,
// }

const loading = false;
</script>
