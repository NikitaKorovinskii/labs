<template>
   <KorovinskiiComponent></KorovinskiiComponent>
   <!-- <Vyatsu :results="results"></Vyatsu> -->
   <Regestration></Regestration>
    <!-- <Avtoreg></Avtoreg> -->
    <Dasboard></Dasboard>

</template>

<script>
import KorovinskiiComponent from 'korovinskii-component';
import Regestration from 'regestration';
import axios from 'axios';
// import Avtoreg from 'avtoreg';
// import Vyatsu from 'vytsu';
import Dasboard from 'dasboard';

const url = 'http://localhost:8080/admission/';

export default {
  components: {
    KorovinskiiComponent,
    // Vyatsu,
    Regestration,
    // Avtoreg,
    Dasboard,
  },
  data() {
    return { KorovinskiiComponent, results: [] };
  },
  mounted() {
    axios
      .get(url)
      .then((response) => {
        console.log(response);
        this.results = response.data;
      })
      .catch((error) => console.log(error));
  },
};
</script>

<style>
</style>
