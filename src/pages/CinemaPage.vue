<template>
  <q-page class="row items-center justify-evenly text-brand">
    <q-form
      class="column q-px-xl q-py-md shadow-2 bg-blue-1"
      action=""
      method=""
      @submit="submitForm"
    >
      <q-input
        name="location"
        placeholder="Cinema Location"
        v-model="form.location"
      />
      <div class="q-mt-md"> 
        <p>Cinema Numbers</p>
        <div>
          <q-checkbox v-model="form.cinemaNum" label="1" val="1" />
          <q-checkbox v-model="form.cinemaNum" label="2" val="2" />
          <q-checkbox v-model="form.cinemaNum" label="3" val="3" />
          <q-checkbox v-model="form.cinemaNum" label="4" val="4" />
          <q-checkbox v-model="form.cinemaNum" label="5" val="5" />
          <q-checkbox v-model="form.cinemaNum" label="6" val="6" />
          <q-checkbox v-model="form.cinemaNum" label="7" val="7" />
          <q-checkbox v-model="form.cinemaNum" label="8" val="8" />
        </div>
      </div>

      <q-file
        class="q-mt-md"
        outlined
        v-model="form.cinemaPosterURL"
        name="cinemaPosterURL"
        label="Attach Cinema Logo"
        accept="image/*"
      >
        <template v-slot:prepend>
          <q-icon name="attach_file" />
        </template>
      </q-file>

      <q-btn class="q-mt-xl" label="Add Movie" type="submit" color="green" />
    </q-form>

    <!-- CINEMA LIST TABLE -->
    <q-table
      title="Cinema List"
      :rows="cinemaData"
      :columns="columns"
      row-key="name"
    />
  </q-page>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const form = ref({
  location: '',
  cinemaNum: [],
  cinemaPosterURL: '/assets/smcinema.png',
});

// const requireValue = (val) => (val && val.length > 0) || 'Invalid Input'

const cinemaData = [
  {
    location: 'SM Cubao',
    cinemaPosterURL: 'smcinema.png',
    cinemaNum: [2, 5],
  },
  {
    location: 'SM Nort Edsa',
    cinemaPosterURL: 'smcinema.png',
    cinemaNum: [1, 2, 3],
  },
];

const submitForm = (event) => {
  event.preventDefault();

  cinemaData.unshift({
    location: form.value.location,
    cinemaNum: form.value.cinemaNum,
    cinemaPosterURL: form.value.cinemaPosterURL,
  });
  console.log(cinemaData);

  form.value.location = '';
  form.value.cinemaNum = [];
  form.value.cinemaPosterURL = '/assets/smcinema.png';
};

const columns = [
  {
    name: 'Location',
    field: 'location',
    label: 'Location',
    align: 'left',
    sortable: true,
  },
  {
    name: 'Cinemas',
    field: 'cinemaNum',
    label: 'Cinema Number',
    align: 'center',
  },
  {
    name: 'Icon',
    field: 'cinemaPosterURL',
    label: 'Logo URL',
    align: 'center',
  },
];
</script>

<style>
.text-brand {
  background: linear-gradient(116.82deg, #000000 50%, #575757 100%), #ffffff;
}
</style>
